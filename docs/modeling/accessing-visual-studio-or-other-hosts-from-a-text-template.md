---
title: Dostęp do Visual Studio lub innych hostów z szablonu tekstowego
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9bb7bce5cb047018540599c9488fa4471dad2d1c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059301"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Dostęp do programu Visual Studio lub innych hostów z szablonu tekstowego

W szablonie tekstu można użyć metod i właściwości, które są udostępniane przez hosta, który jest wykonywany szablonu. Program Visual Studio jest przykładem hosta.

> [!NOTE]
> W szablonach zwykły tekst, ale nie można użyć właściwości i metod hosta *wstępnie przetworzony* szablonów tekstowych.

## <a name="obtain-access-to-the-host"></a>Uzyskaj dostęp do hosta

Aby uzyskać dostęp do hosta, należy ustawić `hostspecific="true"` w `template` dyrektywy. Teraz możesz używać `this.Host`, która ma typ <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Typ ma elementów członkowskich, które umożliwia, na przykład, rozpoznawanie nazw plików i rejestrowanie błędów.

### <a name="resolve-file-names"></a>Rozpoznawanie nazw plików

Aby znaleźć pełnej ścieżki pliku względem szablonu tekstu, należy użyć `this.Host.ResolvePath()`.

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

### <a name="display-error-messages"></a>Wyświetlane komunikaty o błędach

W tym przykładzie powoduje rejestrowanie komunikatów podczas przekształcania szablonu. Jeśli host znajduje się program Visual Studio, błędy są dodawane do **lista błędów**.

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

## <a name="use-the-visual-studio-api"></a>Za pomocą programu Visual Studio interfejsu API

Jeśli wykonujesz szablonu tekstu w programie Visual Studio, możesz użyć `this.Host` dostęp do usług świadczonych przez program Visual Studio i wszystkie pakiety lub rozszerzenia, które są ładowane.

Ustaw hostspecific = "true" i rzutowane `this.Host` do <xref:System.IServiceProvider>.

W tym przykładzie pobiera do API Visual Studio <xref:EnvDTE.DTE>, jako usługi:

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

## <a name="use-hostspecific-with-template-inheritance"></a>HostSpecific za pomocą szablonu dziedziczenia

Określ `hostspecific="trueFromBase"` , gdy również użyć `inherits` atrybutu, a jeśli dziedziczyć szablon, który określa `hostspecific="true"`. Jeśli nie masz, możesz otrzymać kompilatora ostrzeżenie, że właściwość `Host` zadeklarowano dwa razy.