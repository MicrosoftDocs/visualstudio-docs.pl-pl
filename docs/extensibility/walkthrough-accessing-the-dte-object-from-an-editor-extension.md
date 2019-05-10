---
title: Dostęp do obiektu DTE z rozszerzenia Edytora
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3e21ea3d05350a59d62fc9da9e0387f072ec16
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878199"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Przewodnik: Dostęp do obiektu DTE z rozszerzenia Edytora

Obiekt DTE w pakietach VSPackage, można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody z typem obiektu DTE. W rozszerzeniach Managed Extensibility Framework (MEF), można zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , a następnie wywołać <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody z typem <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Pobierz obiekt DTE

1. Tworzenie C# VSIX projektu i nadaj mu nazwę **DTETest**. Dodaj **klasyfikatora edytora** szablonu elementu i nadaj mu nazwę **DTETest**.

   Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Dodaj następujące odwołanie do zestawu do projektu:

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. W *DTETestProvider.cs* plików, Dodaj następujący kod `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasy, import <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metody, Dodaj następujący kod przed `return` instrukcji:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Dodaj następujące odwołania do zestawów do projektu:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. W *DTETestProvider.cs* plików, Dodaj następujący kod `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasy, import <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metody, Dodaj następujący kod przed `return` instrukcji:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)
- [Uruchom program Visual Studio przy użyciu DTE](launch-visual-studio-dte.md)