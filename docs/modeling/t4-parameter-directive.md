---
title: Dyrektywa T4 dotycząca parametru
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 42853082ef5de6027bdfb897e85f04d2bc37ad7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868738"
---
# <a name="t4-parameter-directive"></a>Dyrektywa T4 dotycząca parametru

W szablonie tekstu Visual Studio `parameter` dyrektywy deklaruje właściwości w kodzie szablonu, które są inicjowane od wartości przekazanej w kontekście zewnętrznych. Te wartości można ustawić, jeśli piszesz kod, który wywołuje przekształcenia tekstu.

## <a name="using-the-parameter-directive"></a>Użycie dyrektywy parametru

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter` Dyrektywy deklaruje właściwości w kodzie szablonu, które są inicjowane od wartości przekazanej w kontekście zewnętrznych. Te wartości można ustawić, jeśli piszesz kod, który wywołuje przekształcenia tekstu. Wartości mogą być przekazywane w `Session` słownika, lub <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Możesz deklarować parametrów dowolnego typu może być zastosowana zdalnie. Oznacza to, że typ musi być zadeklarowany z <xref:System.SerializableAttribute>, lub musi pochodzić od <xref:System.MarshalByRefObject>. Dzięki temu wartości parametrów do przekazania do elementu AppDomain, w którym szablon jest przetwarzany.

 Na przykład można napisać szablon tekstowy o następującej zawartości:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Przekazywanie wartości parametrów do szablonu
 Jeśli piszesz rozszerzenia programu Visual Studio, takie jak polecenie menu lub program obsługi zdarzeń może przetwarzać szablonu przy użyciu usługi szablonów tekstowych:

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

## <a name="passing-values-in-the-call-context"></a>Mechanizm przekazywania wartości w kontekście wywołań
 Można również przekazać wartości danych logicznych w <xref:System.Runtime.Remoting.Messaging.CallContext>.

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Przekazanie wartości do szablonu tekstu czasu wykonywania (preprocesora)
 Nie jest zazwyczaj konieczne jest użycie `<#@parameter#>` dyrektywy przy użyciu szablonów tekstowych (wstępnie przetworzony) czasu wykonywania. Zamiast tego można zdefiniować dodatkowe Konstruktor lub właściwości do ustawienia dla wygenerowanego kodu, za pomocą których możesz podać wartości parametrów. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Jednakże jeśli chcesz używać `<#@parameter>` w szablonie czasu wykonywania, można przekazać wartości do niego za pomocą słownika sesji. Na przykład załóżmy, że plik został utworzony jako wstępnie przetworzony szablon o nazwie `PreTextTemplate1`. Szablon można wywołać w swoim programie przy użyciu następującego kodu.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Uzyskiwanie argumenty z TextTemplate.exe

> [!IMPORTANT]
>  `parameter` Dyrektywy nie pobrać wartości ustawione w `-a` parametru `TextTransform.exe` narzędzia. Aby uzyskać te wartości, należy ustawić `hostSpecific="true"` w `template` dyrektywy i użyj `this.Host.ResolveParameterValue("","","argName")`.