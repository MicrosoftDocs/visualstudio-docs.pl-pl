---
title: Uzyskiwanie dostępu do programu Visual Studio 2015 lub innych hostów z szablonu tekstu | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d26c168780051d3644d04d209001bf0cc9a551cb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796799"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Dostęp do Visual Studio lub innych hostów z szablonu tekstowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W szablonie tekstu, można użyć metod i właściwości udostępniane przez hosta, który jest wykonywany szablonu, takie jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Dotyczy to zwykły tekst szablonów, szablony nieprzetworzony tekst.

## <a name="obtaining-access-to-the-host"></a>Uzyskiwanie dostępu do hosta
 Ustaw `hostspecific="true"` w `template` dyrektywy. Dzięki temu można używać `this.Host`, która ma typ <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Ten typ ma elementów członkowskich, które umożliwia, na przykład, aby rozpoznać nazwy pliku i rejestrować błędy.

### <a name="resolving-file-names"></a>Rozpoznawanie nazw plików
 Aby uzyskać pełną ścieżkę pliku względem szablonu tekstu, użyj tego. Host.ResolvePath().

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
 W tym przykładzie powoduje rejestrowanie komunikatów podczas przekształcania szablonu. Jeśli host znajduje się [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zostaną one dodane do okna błędu.

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

## <a name="using-the-visual-studio-api"></a>Za pomocą programu Visual Studio API
 Jeśli są wykonywane szablonu tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], możesz użyć `this.Host` dostęp do usług świadczonych przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i pakietów lub rozszerzenia, które są ładowane.

 Ustaw hostspecific = "true" i rzutowane `this.Host` do <xref:System.IServiceProvider>.

 W tym przykładzie pobiera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu API, <xref:EnvDTE.DTE>, jako usługi:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Przy użyciu dziedziczenia szablonu hostSpecific
 Określ `hostspecific="trueFromBase"` , gdy również użyć `inherits` atrybutu, a jeśli dziedziczyć szablon, który określa `hostspecific="true"`. Pozwala to uniknąć ostrzeżenia kompilatora dla efektu, właściwość `Host` zadeklarowano dwa razy.
