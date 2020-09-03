---
title: 'Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148876"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Przewodnik: uzyskiwanie dostępu do obiektu DTE z rozszerzenia edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W pakietów VSPackage można uzyskać obiekt DTE przez wywołanie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody z typem obiektu DTE. W Managed Extensibility Framework (MEF) rozszerzenia można zaimportować, <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a następnie wywołać <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodę z typem <xref:EnvDTE.DTE> .  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Pobieranie obiektu DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Aby pobrać obiekt DTE z  
  
1. Utwórz projekt w języku C# o nazwie `DTETest` . Dodaj szablon elementu klasyfikatora edytora i nadaj mu nazwę `DTETest` . Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2. Dodaj do projektu następujące odwołania do zestawu:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. Shell. unzmienny. 10.0  
  
3. Przejdź do pliku DTETest.cs i Dodaj następujące `using` dyrektywy:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. W `GetDTEProvider` klasie zaimportuj <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. W `GetClassifier()` metodzie Dodaj następujący kod.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. Jeśli konieczne jest użycie <xref:EnvDTE80.DTE2> interfejsu, można rzutować obiekt DTE.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
