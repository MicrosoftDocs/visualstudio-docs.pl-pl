---
title: Sekwencja inicjowania podtypów projektów | Dokumentacja firmy Microsoft
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
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53c0a474a5a5caf887599bc50e623bd25e7be782
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746524"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sekwencja inicjowania podtypów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Środowisko konstruuje projekt przez wywołanie wykonania fabryka projektu podstawowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Konstrukcja podtypu projektu rozpoczyna się, gdy środowisko określa, czy listy identyfikatorów GUID typu projektu rozszerzenia pliku projektu nie jest pusty. Rozszerzenie pliku projektu i identyfikator GUID projektu określają, czy projekt jest [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../includes/csprcs-md.md)] typ projektu. Na przykład rozszerzenie .vbproj i zidentyfikować {F184B08F-C81C-45F6-A57F-5ABD9991F28F} [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektu.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Inicjowanie środowiska podtypów projektów  
 W poniższej procedurze szczegółowo Sekwencja inicjowania systemu projektu agregowane przez wiele podtypy projektów.  
  
1. Środowisko wywołuje projektu podstawowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, a gdy projekt analizowania jego pliku projektu odnajduje nie jest typem projektu agregacji listy identyfikatorów GUID `null`. Projekt zaprzestaje bezpośrednio tworzenie swoich projektów.  
  
2. Wywoływanych w projekcie `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> Usługa do tworzenia podtypem projektu przy użyciu implementacji środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody. W ramach tej metody środowiska sprawia, że wywołania funkcji rekursywnych do swojej implementacji klasy <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> metody, gdy jest ona zalet listy projektu wpisz identyfikatory GUID, począwszy od podtypu projektu najbardziej zewnętrznej.  
  
    Poniżej przedstawiono kroki inicjowania.  
  
   1.  Implementacja interfejsu środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> wywołania metody "HrCreateInnerProj''" metody z poniższej deklaracji funkcji:  
  
       ```  
       HRESULT HrCreateInnerProj  
       (  
           WCHAR *pwszGuids,  
           IUnknown *pOuter,  
           IVsAggregatableProject *pOwner,  
           LPCOLESTR pszFilename,  
           LPCOLESTR pszLocation,  
           LPCOLESTR pszName,  
           VSCREATEPROJFLAGS grfCreateFlags,  
           IUnknown **ppInner,  
           BOOL *pfCancelled  
       )  
       ```  
  
        Gdy ta funkcja jest wywoływana po raz pierwszy, oznacza to, dla podtypu projektu najbardziej zewnętrznej, parametry `pOuter` i `pOwner` są przekazywane w jako `null` i funkcja ustawia podtypu projektu najbardziej zewnętrznej `IUnknown` do `pOuter`.  
  
   2.  Następnie wywołuje środowisko `HrCreateInnerProj` funkcji z drugi identyfikator GUID typu projektu na liście. Ten identyfikator GUID odnosi się do drugiego podtypu projektu wewnętrznego przechodzenie krok po kroku kierunku projektu podstawowego w sekwencji agregacji.  
  
   3.  `pOuter` Teraz wskazuje `IUnknown` podtypu projektu najbardziej zewnętrznej i `HrCreateInnerProj` implementacja wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> następuje wywołanie do implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metoda przekazywania w kontrolowaniu `IUnknown` podtypu projektu najbardziej zewnętrznej `pOuter`. Należących do projektu (podtypu projektu wewnętrznego) musi utworzyć jego obiekt projektu agregacji. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementacji metody przekazać wskaźnik do `IUnknown` wewnętrzny projektu, który są agregowane. Te dwie metody tworzenia obiektu agregacji, a Twoje implementacje muszą wykonać reguły agregacji COM, aby upewnić się, że podtypu projektu nie znajdą się przytrzymanie licznik odwołań do samej siebie.  
  
   4.  `HrCreateInnerProj` Implementacja wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. W przypadku tej metody podtypu projektu działa inicjowania. Na przykład można rejestrować zdarzenia rozwiązania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
   5.  `HrCreateInnerProj` jest wywoływany rekursywnie, aż do osiągnięcia ostatni identyfikator GUID (podstawowy projekt) na liście. Dla każdego z tych wywołań są powtarzane czynności c do d. `pOuter` Wskazuje podtypu projektu najbardziej zewnętrznej `IUnknown` dla każdego poziomu agregacji.  
  
   W poniższym przykładzie opisano proces programistyczny w przybliżony reprezentacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody jest implementowany przez środowisko. Kod jest tylko przykładowe; nie jest przeznaczone do skompilowania i sprawdzanie błędów wszystkie została usunięta z myślą o przejrzystości.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)

