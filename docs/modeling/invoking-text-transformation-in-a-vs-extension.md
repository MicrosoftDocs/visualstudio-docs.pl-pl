---
title: Wywoływanie transformacji tekstu w rozszerzeniu VS
description: Dowiedz się, jak przekształcać szablony tekstowe za pomocą usługi tworzenia szablonów tekstu. Dowiedz się również, jak pobrać usługę STextTemplating i rzutować ją na ITextTemplating.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71f376cbe0ffd6c2716802977f1570aa5036fcdb
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386777"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>Wywoływanie przekształcenia tekstu w rozszerzeniu Visual Studio danych

Jeśli piszesz rozszerzenie Visual Studio, takie jak polecenie menu lub język specyficzny dla [domeny,](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)możesz użyć usługi tworzenia szablonów tekstu do przekształcania szablonów tekstowych. Pobierz [usługę STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) i rzutuj ją na [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="get-the-text-templating-service"></a>Pobierz usługę szablonów tekstu

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="pass-parameters-to-the-template"></a>Przekaż parametry do szablonu

 Parametry można przekazać do szablonu. Wewnątrz szablonu można uzyskać wartości parametrów przy użyciu `<#@parameter#>` dyrektywy .

 Jeśli chodzi o typ parametru należy użyć typu, który jest możliwy do serializacji lub który może być organizowany. Oznacza to, że typ musi być zadeklarowany za pomocą <xref:System.SerializableAttribute> lub musi pochodzić od <xref:System.MarshalByRefObject> . To ograniczenie jest konieczne, ponieważ szablon tekstowy jest wykonywany w oddzielnym elemencie AppDomain. Wszystkie wbudowane typy, takie jak **System.String** i **System.Int32,** można serializuje.

 Aby przekazać wartości parametrów, kod wywołujący może umieścić wartości w `Session` słowniku lub w pliku <xref:System.Runtime.Remoting.Messaging.CallContext> .

 W poniższym przykładzie użyto obu tych metod, aby przekształcić krótki szablon tekstowy:

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>Raportowanie błędów i dyrektywa wyjściowa

Wszelkie błędy, które wystąpią podczas przetwarzania, zostaną wyświetlone w Visual Studio błędu. Ponadto możesz być powiadamiany o błędach, określając wywołanie zwrotne, które implementuje [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

Jeśli chcesz zapisać ciąg wynikowy do pliku, warto wiedzieć, jakie rozszerzenie pliku i kodowanie zostały określone w `<#@output#>` dyrektywie w szablonie. Te informacje również zostaną przekazane do wywołania zwrotnego. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 Output .](../modeling/t4-output-directive.md)

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

Kod może być testowany z plikiem szablonu, podobnym do następującego:

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

Ostrzeżenie kompilatora zostanie wyświetlone w Visual Studio błędu, a także wygeneruje wywołanie `ErrorCallback` .

## <a name="reference-parameters"></a>Parametry odwołania

Wartości z szablonu tekstowego można przekazać przy użyciu klasy parametrów pochodzącej z klasy <xref:System.MarshalByRefObject> .

## <a name="related-articles"></a>Pokrewne artykuły:

Aby wygenerować tekst na podstawie wstępnie przetworzonego szablonu tekstu: `TransformText()` wywołaj metodę wygenerowanej klasy . Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie uruchamiania za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md)

Aby wygenerować tekst poza rozszerzeniem Visual Studio: definiowanie niestandardowego hosta. Aby uzyskać więcej informacji, zobacz Processing Text Templates by using a Custom Host (Przetwarzanie szablonów [tekstowych przy użyciu hosta niestandardowego).](../modeling/processing-text-templates-by-using-a-custom-host.md)

Aby wygenerować kod źródłowy, który można później skompilować i wykonać: wywołaj metodę [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) dla [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).
