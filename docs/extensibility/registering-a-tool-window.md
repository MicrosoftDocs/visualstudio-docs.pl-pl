---
title: Rejestrowanie okna narzędzi | Microsoft Docs
description: Dowiedz się, jak zarejestrować swoje okna narzędzi w programie Visual Studio przy użyciu atrybutu ProvideToolWindowAttribute i ProvideToolWindowVisibilityAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79f830d0a035dbea503ffbbc05ae30acfeb16766
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837037"
---
# <a name="register-a-tool-window"></a>Rejestrowanie okna narzędzi
Możesz zarejestrować swoje okna narzędzi za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

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

 W powyższym kodzie, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> rejestruje okna `PersistedWindowPane` i `DynamicWindowPane` Narzędzia w programie Visual Studio. Utrwalone okno narzędzi jest zadokowane i z kartami **Eksplorator rozwiązań**, a okno dynamiczne ma domyślną pozycję początkową i rozmiar. Okno dynamiczne jest wykonywane przejściowo, co oznacza, że nie jest tworzone podczas uruchamiania. Spowoduje to zapisanie `DontForceCreate` wartości w `ToolWindows` kluczu rejestru systemowego. Aby uzyskać więcej informacji, zobacz [Konfiguracja wyświetlania okna narzędzi](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015).