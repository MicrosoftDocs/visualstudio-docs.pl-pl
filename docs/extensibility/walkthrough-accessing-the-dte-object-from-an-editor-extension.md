---
title: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora
description: Dowiedz się, jak uzyskać dostęp do obiektu DTE z rozszerzenia edytora, korzystając z przykładowego kodu w tym przewodniku.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 094a37960fa5b32d018eebe3becee4fde43cc392
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905127"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora

W pakietach VSPackage można uzyskać obiekt DTE, wywołując metodę z <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> typem obiektu DTE. W Managed Extensibility Framework (MEF) można zaimportować, a następnie wywołać <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodę z typem <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Wymagania wstępne

Aby postępować zgodnie z tym instruktażem, musisz zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="get-the-dte-object"></a>Uzyskiwanie obiektu DTE

1. Utwórz projekt VSIX w języku C# i nadaj temu projektowi **nazwę DTETest.** Dodaj szablon **elementu klasyfikatora edytora** i nadaj jego **nazwę DTETest.**

   Aby uzyskać więcej informacji, zobacz Create an extension with an editor item template (Tworzenie rozszerzenia [za pomocą szablonu elementu edytora).](../extensibility/creating-an-extension-with-an-editor-item-template.md)

::: moniker range=">=vs-2019"

2. Dodaj następujące odwołania do zestawu do projektu:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. W *pliku DTETestProvider.cs* dodaj następujące `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasie zaimportuj element <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metodzie dodaj następujący kod przed instrukcji `return` :

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Dodaj następujące odwołania do zestawu do projektu:

   - Envdte
   - Microsoft.VisualStudio.Shell.Framework

3. W *pliku DTETestProvider.cs* dodaj następujące `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasie zaimportuj element <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metodzie dodaj następujący kod przed instrukcji `return` :

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Uruchamianie programu Visual Studio przy użyciu DTE](launch-visual-studio-dte.md)
