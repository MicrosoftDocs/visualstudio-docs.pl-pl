---
title: Dyrektywa parametru T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c1849cbccc1a903716ba94d02f47a339d6ce426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658570"
---
# <a name="t4-parameter-directive"></a>Dyrektywa T4 dotycząca parametru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W szablonie tekstu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dyrektywa `parameter` deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazywania z zewnętrznego kontekstu. Możesz ustawić te wartości, jeśli piszesz kod, który wywołuje transformację tekstu.

## <a name="using-the-parameter-directive"></a>Używanie dyrektywy Parameter

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 Dyrektywa `parameter` deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazywania z zewnętrznego kontekstu. Możesz ustawić te wartości, jeśli piszesz kod, który wywołuje transformację tekstu. Wartości mogą być przesyłane w słowniku `Session` lub w <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Można zadeklarować parametry dowolnego typu zdalnego. Oznacza to, że typ musi być zadeklarowany za pomocą <xref:System.SerializableAttribute> lub musi pochodzić od <xref:System.MarshalByRefObject>. Pozwala to na przekazywanie wartości parametrów do domeny AppDomain, w której szablon jest przetwarzany.

 Można na przykład napisać szablon tekstowy z następującą zawartością:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>Przekazywanie wartości parametrów do szablonu
 Jeśli piszesz rozszerzenie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], takie jak polecenie menu lub program obsługi zdarzeń, można przetwarzać szablon przy użyciu usługi Text tworzenia szablonów:

```csharp
// Get a service provider – how you do this depends on the context:
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
 Możesz Alternatywnie przekazać wartości jako dane logiczne w <xref:System.Runtime.Remoting.Messaging.CallContext>.

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Przekazywanie wartości do szablonu tekstu czasu wykonywania (wstępnie przetworzonym)
 Nie jest zazwyczaj konieczne używanie dyrektywy `<#@parameter#>` z szablonami tekstu czasu wykonywania (wstępnie przetworzonym). Zamiast tego można zdefiniować dodatkowy Konstruktor lub właściwość settable dla wygenerowanego kodu, za pomocą którego są przekazywane wartości parametrów. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Jeśli jednak chcesz użyć `<#@parameter>` w szablonie czasu wykonywania, możesz przekazać do niego wartości przy użyciu słownika sesji. Załóżmy na przykład, że plik został utworzony jako wstępnie przetworzony szablon o nazwie `PreTextTemplate1`. Możesz wywołać szablon w programie przy użyciu następującego kodu.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Uzyskiwanie argumentów z texttemplate. exe

> [!IMPORTANT]
> Dyrektywa `parameter` nie pobiera wartości ustawionych w parametrze `–a` narzędzia `TextTransform.exe`. Aby uzyskać te wartości, ustaw `hostSpecific="true"` w dyrektywie `template` i użyj `this.Host.ResolveParameterValue("","","argName")`.
