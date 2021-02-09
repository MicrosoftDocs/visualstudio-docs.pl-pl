---
title: Dostęp do obiektu DTE z rozszerzenia edytora
description: Dowiedz się, jak uzyskać dostęp do obiektu DTE z rozszerzenia edytora za pomocą kodu przykładowego w tym instruktażu.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7228165d49c7f11c15d12086933c473699ef6bc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905590"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora

W pakietów VSPackage można uzyskać obiekt DTE przez wywołanie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody z typem obiektu DTE. W Managed Extensibility Framework (MEF) rozszerzenia można zaimportować, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a następnie wywołać <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodę z typem <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Wymagania wstępne

Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Pobierz obiekt DTE

1. Utwórz projekt w języku C# i nadaj mu nazwę **DTETest**. Dodaj szablon elementu **klasyfikatora edytora** i nadaj mu nazwę **DTETest**.

   Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Dodaj do projektu następujące odwołania do zestawu:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. unzmienny. 10.0

3. W pliku *DTETestProvider.cs* Dodaj następujące `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasie zaimportuj <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metodzie Dodaj następujący kod przed `return` instrukcją:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Dodaj do projektu następujące odwołania do zestawu:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. W pliku *DTETestProvider.cs* Dodaj następujące `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. W `DTETestProvider` klasie zaimportuj <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. W `GetClassifier()` metodzie Dodaj następujący kod przed `return` instrukcją:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Uruchamianie programu Visual Studio przy użyciu DTE](launch-visual-studio-dte.md)
