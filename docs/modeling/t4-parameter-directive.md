---
title: Dyrektywa T4 dotycząca parametru
description: Dowiedz się, że w programie Visual Studio dyrektywa Parameter deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazywania z zewnętrznego kontekstu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe68d31d214ae4be8fca35f1e90e63690f3ad581
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924612"
---
# <a name="t4-parameter-directive"></a>Dyrektywa T4 dotycząca parametru

W szablonie tekstu programu Visual Studio `parameter` dyrektywa deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazywania z zewnętrznego kontekstu. Możesz ustawić te wartości, jeśli piszesz kod, który wywołuje transformację tekstu.

## <a name="using-the-parameter-directive"></a>Używanie dyrektywy Parameter

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`Dyrektywa deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazywania z zewnętrznego kontekstu. Możesz ustawić te wartości, jeśli piszesz kod, który wywołuje transformację tekstu. Wartości mogą być przesyłane w `Session` słowniku lub w <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Można zadeklarować parametry dowolnego typu zdalnego. Oznacza to, że typ musi być zadeklarowany z <xref:System.SerializableAttribute> lub musi pochodzić od <xref:System.MarshalByRefObject> . Pozwala to na przekazywanie wartości parametrów do domeny AppDomain, w której szablon jest przetwarzany.

 Można na przykład napisać szablon tekstowy z następującą zawartością:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Przekazywanie wartości parametrów do szablonu
 Jeśli piszesz rozszerzenie programu Visual Studio, takie jak polecenie menu lub program obsługi zdarzeń, możesz przetwarzać szablon przy użyciu usługi Text tworzenia szablonów:

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));
```

## <a name="passing-values-in-the-call-context"></a>Przekazywanie wartości w kontekście wywołania
 Możesz Alternatywnie przekazać wartości jako dane logiczne w <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Poniższy przykład przekazuje wartości przy użyciu obu metod:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test
```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Przekazywanie wartości do szablonu tekstu w Run-Time (wstępnie przetworzonym)
 Nie jest zazwyczaj konieczne używanie `<#@parameter#>` dyrektywy z szablonami tekstu czasu wykonywania (wstępnie przetworzonym). Zamiast tego można zdefiniować dodatkowy Konstruktor lub właściwość settable dla wygenerowanego kodu, za pomocą którego są przekazywane wartości parametrów. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Jeśli jednak chcesz użyć `<#@parameter>` w szablonie czasu wykonywania, możesz przekazać do niego wartości przy użyciu słownika sesji. Załóżmy na przykład, że plik został utworzony jako wstępnie przetworzony szablon o nazwie `PreTextTemplate1` . Możesz wywołać szablon w programie przy użyciu następującego kodu.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Uzyskiwanie argumentów z TextTemplate.exe

> [!IMPORTANT]
> `parameter`Dyrektywa nie pobiera wartości ustawionych w `-a` parametrze `TextTransform.exe` Narzędzia. Aby uzyskać te wartości, ustaw `hostSpecific="true"` w `template` dyrektywie i Użyj `this.Host.ResolveParameterValue("","","argName")` .
