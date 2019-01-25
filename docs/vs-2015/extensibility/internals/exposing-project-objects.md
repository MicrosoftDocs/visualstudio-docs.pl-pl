---
title: Udostępnianie obiektów projektu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c949d4668089a2cc06543169a1c3ce6619409d9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776400"
---
# <a name="exposing-project-objects"></a>Udostępnianie obiektów projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typy projektów niestandardowych można podać obiektów automatyzacji, aby zezwolić na dostęp do projektu przy użyciu interfejsów automatyzacji. Każdy typ projektu powinien zapewniać standard <xref:EnvDTE.Project> obiektu automatyzacji, który jest dostępny z <xref:EnvDTE.Solution>, który zawiera zbiór wszystkich projektów, które są otwarte w środowisku IDE. Każdy element w projekcie powinien być udostępniane przez <xref:EnvDTE.ProjectItem> obiektu uzyskuje się z czasem <xref:EnvDTE.Project.ProjectItems>. Oprócz tych obiektów automatyzacji w wersji standard projektów można zaoferować obiektów automatyzacji specyficznych dla projektu.  
  
 Możesz utworzyć niestandardowe poziomu głównego obiektów automatyzacji, które mogą uzyskać dostęp z późnym wiązaniem z głównego DTE obiektu przy użyciu `DTE.<customeObjectName>` lub `DTE.GetObject(“<customObjectName>”)`. Na przykład Visual C++ Tworzy kolekcję projektu specyficznego dla projektu C++ o nazwie "VCProjects", której będziesz mieć dostęp, za pomocą obiektu DTE. VCProjects lub DTE. GetObject("VCProjects"). Można również utworzyć Project.Object, która jest unikatowa dla typu projektu Project.CodeModel, które mogą być wyszukiwane w jego najbardziej pochodnego obiektu ProjectItem, który uwidacznia ProjectItem.Object i ProjectItem.FileCodeModel.  
  
 Jest typową Konwencją projekty do udostępnienia jako zbiór projektów niestandardowych, specyficzne dla projektu. Na przykład [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] tworzy kolekcję określonego projektu C++, który można następnie uzyskać dostęp za pomocą `DTE.VCProjects` lub `DTE.GetObject("VCProjects")`. Można również utworzyć `Project.Object`, który jest unikatowy dla typu projektu `Project.CodeModel`, może być odpytywany dla swoich najbardziej pochodnego obiektu `ProjectItem`, który ujawnia `ProjectItem.Object`, a `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Aby współtworzyć obiekt pakietu VSPackage specyficzne dla projektu  
  
1.  Dodaj odpowiednie klucze do Twojego pakietu VSPackage plik .pkgdef.  
  
     Na przykład poniżej przedstawiono ustawienia .pkgdef dla projektów języka C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Wdrożyć kod w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody, jak w poniższym przykładzie.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     W kodzie `g_wszAutomationProjects` jest nazwą kolekcji projektów. `GetAutomationProjects` Metoda tworzy obiekt, który implementuje `Projects` interfejsu i zwraca `IDispatch` wskaźnik do obiektu wywołującego, jak pokazano w poniższym przykładzie kodu.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Należy wybrać unikatową nazwę dla obiektu automatyzacji. Konflikty nazw są nieprzewidywalne i kolizji powodują konflikt nazwy obiektów arbitralnie zostanie wygenerowany użycie tej samej nazwie, wiele typów projektów. Należy dołączyć nazwę firmy lub niektóre unikatowe aspekty jego nazwę produktu, nazwę obiektu automatyzacji.  
  
     Niestandardowy `Projects` obiekt kolekcji jest punktem wejścia jako udogodnienie dla pozostałej części projektu modelu automatyzacji. Obiekt projektu jest także dostępny z <xref:EnvDTE.Solution> kolekcji projektów. Po utworzeniu odpowiedni kod i wpisy rejestru, które zapewniają klientom `Projects` obiekty kolekcji implementacji należy podać pozostałe standardowe obiekty modelu projektu. Aby uzyskać więcej informacji, zobacz [projektu modelowania](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
