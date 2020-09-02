---
title: Uzyskiwanie dostępu do programu Visual Studio 2015 lub innych hostów z szablonu tekstu | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655328"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Dostęp do Visual Studio lub innych hostów z szablonu tekstowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W szablonie tekstowym można użyć metod i właściwości uwidocznionych przez hosta, który wykonuje szablon, na przykład [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Dotyczy to zwykłych szablonów tekstu, a nie wstępnie przetworzonych szablonów tekstowych.

## <a name="obtaining-access-to-the-host"></a>Uzyskiwanie dostępu do hosta

Ustaw `hostspecific="true"` w `template` dyrektywie. Umożliwia to korzystanie  `this.Host` z programu, który jest typu [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Ten typ ma elementy członkowskie, których można użyć, na przykład do rozpoznawania nazw plików i rejestrowania błędów.

### <a name="resolving-file-names"></a>Rozpoznawanie nazw plików
 Aby znaleźć pełną ścieżkę pliku względem szablonu tekstu, użyj tego elementu. Host. ResolvePath ().

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

### <a name="displaying-error-messages"></a>Wyświetlanie komunikatów o błędach
 Ten przykład rejestruje komunikaty podczas przekształcania szablonu. Jeśli host jest [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , są dodawane do okna błędu.

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

## <a name="using-the-visual-studio-api"></a>Korzystanie z interfejsu API programu Visual Studio
 W przypadku wykonywania szablonu tekstu w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można użyć programu `this.Host` w celu uzyskania dostępu do usług świadczonych przez program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oraz wszelkich załadowanych pakietów lub rozszerzeń.

 Ustaw hostspecific = "true" i przerzutowanie `this.Host` na <xref:System.IServiceProvider> .

 Ten przykład pobiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejs API, <xref:EnvDTE.DTE> , jako usługę:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Używanie hostSpecific z dziedziczeniem szablonów
 Określ `hostspecific="trueFromBase"` , czy należy również użyć `inherits` atrybutu, i jeśli dziedziczysz z szablonu, który określa `hostspecific="true"` . Pozwala to uniknąć ostrzeżenia kompilatora, że właściwość została `Host` zadeklarowana dwukrotnie.
