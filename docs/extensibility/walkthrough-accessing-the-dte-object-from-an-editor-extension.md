---
title: Dostęp do obiektu DTE z rozszerzenia edytora
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269090"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora

W pakietów VSPackage można uzyskać obiekt DTE, wywołując metodę <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> z typem obiektu DTE. W rozszerzeniach Managed Extensibility Framework (MEF) można zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a następnie wywołać metodę <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> z typem <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Wymagania wstępne

Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Pobierz obiekt DTE

1. Utwórz projekt C# VSIX i nadaj mu nazwę **DTETest**. Dodaj szablon elementu **klasyfikatora edytora** i nadaj mu nazwę **DTETest**.

   Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Dodaj do projektu następujące odwołania do zestawu:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. unzmienny. 10.0

3. W pliku *DTETestProvider.cs* Dodaj następujące dyrektywy `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W klasie `DTETestProvider` zaimportuj <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W metodzie `GetClassifier()` Dodaj następujący kod przed instrukcją `return`:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Dodaj do projektu następujące odwołania do zestawu:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. W pliku *DTETestProvider.cs* Dodaj następujące dyrektywy `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W klasie `DTETestProvider` zaimportuj <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W metodzie `GetClassifier()` Dodaj następujący kod przed instrukcją `return`:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Uruchamianie programu Visual Studio przy użyciu DTE](launch-visual-studio-dte.md)
