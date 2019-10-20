---
title: Dostęp do Visual Studio lub innych hostów z szablonu tekstowego
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652365"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Dostęp do programu Visual Studio lub innych hostów z szablonu tekstowego

W szablonie tekstowym można użyć metod i właściwości, które są dostępne dla hosta, który wykonuje szablon. Visual Studio to przykład hosta.

> [!NOTE]
> Metod hosta i właściwości można użyć w zwykłych szablonach tekstowych, ale nie w szablonach *wstępnie przetworzonych* tekstu.

## <a name="obtain-access-to-the-host"></a>Uzyskaj dostęp do hosta

Aby uzyskać dostęp do hosta, ustaw `hostspecific="true"` w dyrektywie `template`. Teraz można użyć `this.Host`, który ma typ [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Typ [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) zawiera elementy członkowskie, których można użyć do rozpoznawania nazw plików i błędów dzienników, na przykład.

### <a name="resolve-file-names"></a>Rozpoznawanie nazw plików

Aby znaleźć pełną ścieżkę pliku względem szablonu tekstu, użyj `this.Host.ResolvePath()`.

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

### <a name="display-error-messages"></a>Wyświetl komunikaty o błędach

Ten przykład rejestruje komunikaty podczas przekształcania szablonu. Jeśli hostem jest program Visual Studio, błędy są dodawane do **Lista błędów**.

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

## <a name="use-the-visual-studio-api"></a>Korzystanie z interfejsu API programu Visual Studio

Jeśli wykonujesz szablon tekstowy w programie Visual Studio, możesz użyć `this.Host`, aby uzyskać dostęp do usług oferowanych przez program Visual Studio i wszystkich załadowanych pakietów lub rozszerzeń.

Ustaw hostspecific = "true" i Cast `this.Host`, aby <xref:System.IServiceProvider>.

Ten przykład pobiera interfejs API programu Visual Studio, <xref:EnvDTE.DTE>, jako usługę:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Korzystanie z hostSpecific z dziedziczeniem szablonów

Określ `hostspecific="trueFromBase"`, jeśli używasz również atrybutu `inherits`, i jeśli dziedziczysz z szablonu, który określa `hostspecific="true"`. Jeśli tego nie zrobisz, możesz uzyskać Ostrzeżenie kompilatora, że właściwość `Host` została zadeklarowana dwukrotnie.