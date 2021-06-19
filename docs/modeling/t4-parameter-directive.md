---
title: Dyrektywa T4 dotycząca parametru
description: Dowiedz się, Visual Studio, dyrektywa parameter deklaruje właściwości w kodzie szablonu, które są zainicjowane na podstawie wartości przekazywanych z kontekstu zewnętrznego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386101"
---
# <a name="t4-parameter-directive"></a>Dyrektywa T4 dotycząca parametru

W szablonie Visual Studio tekstowym dyrektywa deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazywanych `parameter` z kontekstu zewnętrznego. Te wartości można ustawić, jeśli napiszesz kod, który wywołuje przekształcenie tekstu.

## <a name="using-the-parameter-directive"></a>Korzystanie z dyrektywy Parameter

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 Dyrektywa `parameter` deklaruje właściwości w kodzie szablonu, które są inicjowane na podstawie wartości przekazywanych z kontekstu zewnętrznego. Te wartości można ustawić, jeśli napiszesz kod, który wywołuje przekształcenie tekstu. Wartości mogą być przekazywane w słowniku `Session` lub w pliku <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Możesz zadeklarować parametry dowolnego typu komunikacji zdalnej. Oznacza to, że typ musi być zadeklarowany za pomocą <xref:System.SerializableAttribute> lub musi pochodzić od <xref:System.MarshalByRefObject> . Dzięki temu wartości parametrów mogą być przekazywane do domeny aplikacji, w której szablon jest przetwarzany.

 Można na przykład napisać szablon tekstowy o następującej zawartości:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Przekazywanie wartości parametrów do szablonu
 Jeśli piszesz rozszerzenie Visual Studio, takie jak polecenie menu lub program obsługi zdarzeń, możesz przetworzyć szablon przy użyciu usługi tworzenia szablonów tekstu:

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
 Możesz też przekazać wartości jako dane logiczne w programie <xref:System.Runtime.Remoting.Messaging.CallContext> .

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Przekazywanie wartości do szablonu Run-Time (wstępnie przetworzonego)
 Zazwyczaj nie jest konieczne używanie dyrektywy z szablonami tekstami w czasie `<#@parameter#>` działania (wstępnie przetworzonymi). Zamiast tego można zdefiniować dodatkowy konstruktor lub ustawianą właściwość dla wygenerowanego kodu, za pomocą którego są przekazywać wartości parametrów. Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie uruchamiania za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md)

 Jeśli jednak chcesz użyć szablonu w czasie rzeczywistym, możesz przekazać do niego wartości przy użyciu `<#@parameter>` słownika Session. Załóżmy na przykład, że utworzono plik jako wstępnie przetworzony szablon o nazwie `PreTextTemplate1` . Szablon w programie można wywołać przy użyciu poniższego kodu.

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
> Dyrektywa `parameter` nie pobiera wartości ustawionych w `-a` parametrze narzędzia `TextTransform.exe` . Aby uzyskać te wartości, ustaw `hostSpecific="true"` w `template` dyrektywie i użyj . `this.Host.ResolveParameterValue("","","argName")`
