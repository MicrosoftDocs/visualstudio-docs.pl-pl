---
title: 'Przewodnik: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia Edytora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 011e62af5c836eab4d59e5262774c53be3807638
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718313"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Przewodnik: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia Edytora
Obiekt DTE w pakietach VSPackage, można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody z typem obiektu DTE. W rozszerzeniach Managed Extensibility Framework (MEF), można zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , a następnie wywołać <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody z typem <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="getting-the-dte-object"></a>Pobieranie obiektu DTE

### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Aby uzyskać obiekt DTE z element ServiceProvider

1.  Utwórz projekt VSIX języka C# o nazwie `DTETest`. Dodaj szablon elementu klasyfikatora edytora i nadaj mu nazwę `DTETest`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

2.  Dodaj następujące odwołania do zestawów do projektu:

    -   EnvDTE

    -   EnvDTE80

    -   Microsoft.VisualStudio.Shell.Immutable.10.0

3.  Przejdź do *DTETest.cs* pliku i Dodaj następujący kod `using` dyrektywy:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio.Shell;

    ```

4.  W `GetDTEProvider` klasy, import <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;

    ```

5.  W `GetClassifier()` metody, Dodaj następujący kod.

    ```csharp
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));

    ```

6.  Jeśli trzeba użyć <xref:EnvDTE80.DTE2> interfejsu, można rzutować obiektu DTE do niego.

## <a name="see-also"></a>Zobacz także
- [Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)