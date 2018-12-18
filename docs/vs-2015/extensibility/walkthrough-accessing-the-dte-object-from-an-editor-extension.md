---
title: 'Wskazówki: Uzyskiwanie dostępu do obiektu DTE z rozszerzenia Edytora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b86f33390068b04d9e54c0022e8adeb77ed4700f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720768"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obiekt DTE w pakietach VSPackage, można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody z typem obiektu DTE. W rozszerzeniach Managed Extensibility Framework (MEF), można zaimportować <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , a następnie wywołać <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody z typem <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Pobieranie obiektu DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Aby uzyskać obiekt DTE z element ServiceProvider  
  
1.  Utwórz projekt VSIX języka C# o nazwie `DTETest`. Dodaj szablon elementu klasyfikatora edytora i nadaj mu nazwę `DTETest`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Dodaj następujące odwołania do zestawów do projektu:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Przejdź do pliku DTETest.cs i dodaj następującą `using` dyrektywy:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)

