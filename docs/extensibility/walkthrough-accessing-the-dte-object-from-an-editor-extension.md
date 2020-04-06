---
title: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697663"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Instruktaż: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora

W vspackages, można uzyskać DTE obiektu <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> wywołując metodę z typem obiektu DTE. W rozszerzeniach mef (Managed Extensibility Framework) można <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> importować, a <xref:EnvDTE.DTE>następnie wywoływać metodę z typem .

## <a name="prerequisites"></a>Wymagania wstępne

Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Pobierz obiekt DTE

1. Utwórz projekt VSIX w języku C# i nadaj jego nazwę **DTETest**. Dodaj szablon elementu **klasyfikatora edytora** i nadaj jego nazwę **DTETest**.

   Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Dodaj następujące odwołania do zestawu do projektu:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Niezmienne.10.0

3. W pliku *DTETestProvider.cs* dodaj następujące `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasie zaimportuj plik <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metodzie dodaj następujący kod `return` przed instrukcją:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Dodaj następujące odwołania do zestawu do projektu:

   - Envdte
   - Microsoft.VisualStudio.Shell.Framework

3. W pliku *DTETestProvider.cs* dodaj następujące `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasie zaimportuj plik <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metodzie dodaj następujący kod `return` przed instrukcją:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Uruchamianie programu Visual Studio przy użyciu DTE](launch-visual-studio-dte.md)
