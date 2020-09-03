---
title: Udostępnianie obiektów projektu | Microsoft Docs
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
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196644"
---
# <a name="exposing-project-objects"></a>Udostępnianie obiektów projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Niestandardowe typy projektów mogą zapewniać obiekty automatyzacji, aby zezwolić na dostęp do projektu za pomocą interfejsów automatyzacji. Każdy typ projektu jest oczekiwany do udostępnienia standardowego <xref:EnvDTE.Project> obiektu automatyzacji, do którego jest uzyskiwany dostęp z <xref:EnvDTE.Solution> , który zawiera kolekcję wszystkich projektów, które są otwarte w IDE. Każdy element w projekcie powinien być uwidoczniony przez <xref:EnvDTE.ProjectItem> obiekt, do którego można uzyskać dostęp za pomocą <xref:EnvDTE.Project.ProjectItems> . Oprócz tych standardowych obiektów automatyzacji projekty mogą oferować obiekty automatyzacji specyficzne dla projektu.  
  
 Można utworzyć niestandardowe obiekty automatyzacji na poziomie głównym, do których można uzyskać dostęp z późnym wiązaniem z głównego obiektu DTE przy użyciu `DTE.<customeObjectName>` lub `DTE.GetObject(“<customObjectName>”)` . Na przykład Visual C++ tworzy kolekcję projektów specyficzną dla projektu C++ o nazwie "VCProjects", do której można uzyskać dostęp przy użyciu DTE. VCProjects lub DTE. GetObject ("VCProjects"). Można również utworzyć obiekt Project. Object, który jest unikatowy dla typu projektu, projektu. CodeModel, który może być zapytania dla jego najbardziej pochodnego obiektu, ProjectItem, który uwidacznia ProjectItem. Object i ProjectItem. FileCodeModel.  
  
 Jest to wspólna Konwencja dla projektów, która umożliwia uwidocznienie niestandardowej kolekcji projektów specyficznych dla projektu. Na przykład program [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] tworzy kolekcję projektu specyficzną dla języka C++, do której można uzyskać dostęp przy użyciu `DTE.VCProjects` lub `DTE.GetObject("VCProjects")` . Można również utworzyć obiekt `Project.Object` , który jest unikatowy dla typu projektu, a `Project.CodeModel` , który może być zapytania dla jego najbardziej pochodnego obiektu, a `ProjectItem` , który uwidacznia `ProjectItem.Object` i `ProjectItem.FileCodeModel` .  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Aby współtworzyć obiekt specyficzny dla pakietu VSPackage dla projektu  
  
1. Dodaj odpowiednie klucze do pliku pkgdef pakietu VSPackage.  
  
     Na przykład poniżej przedstawiono ustawienia. pkgdef dla projektu języka C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. Zaimplementuj kod w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodzie, tak jak w poniższym przykładzie.  
  
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
  
     W kodzie, `g_wszAutomationProjects` jest nazwą kolekcji projektu. `GetAutomationProjects`Metoda tworzy obiekt, który implementuje `Projects` interfejs i zwraca `IDispatch` wskaźnik do obiektu wywołującego, jak pokazano w poniższym przykładzie kodu.  
  
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
  
     Należy wybrać unikatową nazwę obiektu automatyzacji. Konflikty nazw są nieprzewidywalne, a kolizje powodują arbitralne zgłaszanie sprzecznych nazw obiektów, jeśli wiele typów projektów używa tej samej nazwy. Należy podać nazwę firmy lub unikatowy aspekt nazwy produktu w nazwie obiektu automatyzacji.  
  
     `Projects`Obiekt kolekcji niestandardowej jest wygodnym punktem wejścia dla pozostałej części modelu automatyzacji projektu. Obiekt projektu jest również dostępny z <xref:EnvDTE.Solution> kolekcji projektu. Po utworzeniu odpowiedniego kodu i wpisów rejestru, które dostarczają odbiorców z `Projects` obiektami kolekcji, implementacja musi udostępniać pozostałe obiekty standardowe dla modelu projektu. Aby uzyskać więcej informacji, zobacz artykuł [Modeling Project](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
