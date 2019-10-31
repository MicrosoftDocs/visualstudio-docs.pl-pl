---
title: Rejestrowanie okna narzędzi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34fddd6513aad612398c700b935c6d1d3ee72b59
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186266"
---
# <a name="register-a-tool-window"></a>Rejestrowanie okna narzędzi
Możesz zarejestrować swoje okna narzędzi przy użyciu <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>.

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

 W powyższym kodzie <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> rejestruje okna narzędzi `PersistedWindowPane` i `DynamicWindowPane` przy użyciu programu Visual Studio. Utrwalone okno narzędzi jest zadokowane i z kartami **Eksplorator rozwiązań**, a okno dynamiczne ma domyślną pozycję początkową i rozmiar. Okno dynamiczne jest wykonywane przejściowo, co oznacza, że nie jest tworzone podczas uruchamiania. Spowoduje to zapisanie wartości `DontForceCreate` w kluczu `ToolWindows` w rejestrze systemowym. Aby uzyskać więcej informacji, zobacz [Konfiguracja wyświetlania okna narzędzi](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015).
