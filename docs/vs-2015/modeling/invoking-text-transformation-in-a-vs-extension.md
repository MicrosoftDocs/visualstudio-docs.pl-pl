---
title: Wywoływanie transformacji tekstu w rozszerzeniu programu VS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a87f84a945d9d79f6d481f7bcc9e656f7ec7bcbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646148"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Wywoływanie transformacji tekstu w rozszerzeniu VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli piszesz [rozszerzenie programu Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14) , takie jak polecenie menu lub [Język specyficzny dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), możesz użyć usługi Text tworzenia szablonów do przekształcania szablonów tekstowych. Pobierz usługę [STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) i przerzutj ją na [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="getting-the-text-templating-service"></a>Pobieranie usługi szablonów tekstowych

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));

```

## <a name="passing-parameters-to-the-template"></a>Przekazywanie parametrów do szablonu
 Parametry można przekazać do szablonu. Wewnątrz szablonu można uzyskać wartości parametrów za pomocą dyrektywy `<#@parameter#>`.

 Jeśli chodzi o typ parametru należy użyć typu, który jest możliwy do serializacji lub który może być organizowany. Oznacza to, że typ musi być zadeklarowany za pomocą <xref:System.SerializableAttribute> lub musi pochodzić od <xref:System.MarshalByRefObject>. To ograniczenie jest konieczne, ponieważ szablon tekstowy jest wykonywany w oddzielnym elemencie AppDomain. Wszystkie typy wbudowane, takie jak **System. String** i **System. Int32** , można serializować.

 Aby przekazać wartości parametrów, kod wywołujący może umieścić wartości w słowniku `Session` lub <xref:System.Runtime.Remoting.Messaging.CallContext>.

 W poniższym przykładzie użyto obu tych metod, aby przekształcić krótki szablon tekstowy:

```
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
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
 Wszystkie błędy powstające podczas przetwarzania będą wyświetlane w oknie błędu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ponadto można otrzymywać powiadomienia o błędach przez określenie wywołania zwrotnego implementującego [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

 Jeśli chcesz zapisać ciąg wyniku do pliku, warto wiedzieć, jakie rozszerzenie pliku i kodowanie zostały określone w dyrektywie `<#@output#>` w szablonie. Te informacje również zostaną przekazane do wywołania zwrotnego. Aby uzyskać więcej informacji, zobacz [dyrektywa Output T4](../modeling/t4-output-directive.md).

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

 Ostrzeżenie kompilatora pojawi się w oknie błędów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i spowoduje również wygenerowanie wywołania `ErrorCallback`.

## <a name="reference-parameters"></a>Parametry odwołania
 Można przekazać wartości z szablonu tekstu przy użyciu klasy parametrów, która jest pochodną <xref:System.MarshalByRefObject>.

## <a name="related-topics"></a>Tematy pokrewne
 Aby wygenerować tekst na podstawie wstępnie przetworzonego szablonu tekstu: Wywołaj metodę `TransformText()` wygenerowanej klasy. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Aby wygenerować tekst poza rozszerzeniem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]: Zdefiniuj hosta niestandardowego. Aby uzyskać więcej informacji, zobacz [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Aby wygenerować kod źródłowy, który można później skompilować i wykonać: Wywołaj metodę [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) z [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).
