---
title: Dostęp do Visual Studio lub innych hostów z szablonu tekstowego
description: Dowiedz się, jak używać metod i właściwości w szablonie tekstowym, które są udostępniane przez hosta, który wykonuje szablon.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cde4b2afe6d09c3958bbabe7a5669a13f8de8f2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389127"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Uzyskiwanie Visual Studio lub innych hostów z szablonu tekstowego

W szablonie tekstowym można użyć metod i właściwości, które są udostępniane przez hosta, który wykonuje szablon. Visual Studio jest przykładem hosta.

> [!NOTE]
> Metody i właściwości hosta można używać w zwykłych szablonach tekstowych, ale nie w *wstępnie przetworzonych szablonach* tekstowych.

## <a name="obtain-access-to-the-host"></a>Uzyskiwanie dostępu do hosta

Aby uzyskać dostęp do hosta, ustaw `hostspecific="true"` w `template` dyrektywie . Teraz możesz użyć typu `this.Host` , który ma typ [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Typ [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) zawiera elementy członkowskie, których można użyć na przykład do rozpoznawania nazw plików i błędów dziennika.

### <a name="resolve-file-names"></a>Rozwiązywanie nazw plików

Aby znaleźć pełną ścieżkę pliku względem szablonu tekstowego, `this.Host.ResolvePath()` użyj .

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Wyświetlanie komunikatów o błędach

Ten przykład rejestruje komunikaty podczas przekształcania szablonu. Jeśli host jest Visual Studio, błędy są dodawane do **listy błędów**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Korzystanie z interfejsu API Visual Studio API

Jeśli szablon tekstowy jest wykonywany w programie Visual Studio, można użyć programu do uzyskiwania dostępu do usług oferowanych przez usługę Visual Studio i wszelkich `this.Host` załadowanych pakietów lub rozszerzeń.

Ustaw parametr hostspecific="true" i rzutuj `this.Host` na <xref:System.IServiceProvider> wartość .

W tym przykładzie interfejs API Visual Studio, <xref:EnvDTE.DTE> , jako usługa:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Używanie parametru hostSpecific z dziedziczeniem szablonu

Określ, czy używasz również atrybutu , a jeśli dziedziczysz z `hostspecific="trueFromBase"` `inherits` szablonu, który określa `hostspecific="true"` wartość . Jeśli nie, możesz otrzymać ostrzeżenie kompilatora, że właściwość `Host` została zadeklarowana dwukrotnie.
