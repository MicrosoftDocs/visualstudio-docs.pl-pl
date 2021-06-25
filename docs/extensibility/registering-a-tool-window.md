---
title: Rejestrowanie okna narzędzi | Microsoft Docs
description: Dowiedz się, jak zarejestrować okna narzędzi za pomocą Visual Studio ProvideToolWindowAttribute i ProvideToolWindowVisibilityAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4fb6330f913989a69c5d8d28374a40ea14d266d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899098"
---
# <a name="register-a-tool-window"></a>Rejestrowanie okna narzędzi
Okna narzędzi można zarejestrować przy użyciu narzędzi <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Przykład

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 W powyższym kodzie narzędzie rejestruje okna <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> `PersistedWindowPane` narzędzi i w `DynamicWindowPane` Visual Studio. Utrwalone okno narzędzia jest zadokowane i z kartami Eksplorator rozwiązań **,** a okno dynamiczne ma domyślną pozycję początkową i rozmiar. Okno dynamiczne jest przejściowe, co oznacza, że nie jest tworzone podczas uruchamiania. To zapisuje wartość `DontForceCreate` w `ToolWindows` kluczu w rejestrze systemowym. Aby uzyskać więcej informacji, zobacz [Konfiguracja wyświetlania okna narzędzi](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015).