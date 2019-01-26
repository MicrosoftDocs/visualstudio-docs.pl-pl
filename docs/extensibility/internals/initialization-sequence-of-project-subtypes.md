---
title: Sekwencja inicjowania podtypów projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18a60e5589671101471bbb5f82877ce5234215d8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920192"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sekwencja inicjowania podtypów projektów
Środowisko konstruuje projekt przez wywołanie wykonania fabryka projektu podstawowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Konstrukcja podtypu projektu rozpoczyna się, gdy środowisko określa, czy listy identyfikatorów GUID typu projektu rozszerzenia pliku projektu nie jest pusty. Rozszerzenie pliku projektu i identyfikator GUID projektu określają, czy projekt jest [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] typ projektu. Na przykład rozszerzenie .vbproj i zidentyfikować {F184B08F-C81C-45F6-A57F-5ABD9991F28F} [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu.

## <a name="environments-initialization-of-project-subtypes"></a>Inicjowanie środowiska podtypów projektów
 W poniższej procedurze szczegółowo Sekwencja inicjowania systemu projektu agregowane przez wiele podtypy projektów.

1.  Środowisko wywołuje projektu podstawowego <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, a gdy projekt analizowania jego pliku projektu odnajduje nie jest typem projektu agregacji listy identyfikatorów GUID `null`. Projekt zaprzestaje bezpośrednio tworzenie swoich projektów.

2.  Wywoływanych w projekcie `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> Usługa do tworzenia podtypem projektu przy użyciu implementacji środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody. W ramach tej metody środowiska sprawia, że wywołania funkcji rekursywnych do swojej implementacji klasy <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> metody, gdy jest ona zalet listy projektu wpisz identyfikatory GUID, począwszy od podtypu projektu najbardziej zewnętrznej.

     Poniżej przedstawiono kroki inicjowania.

    1.  Implementacja interfejsu środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> wywołania metody `HrCreateInnerProj` metody za pomocą poniższej deklaracji funkcji:

         <CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Gdy ta funkcja jest wywoływana po raz pierwszy, oznacza to, dla podtypu projektu najbardziej zewnętrznej, parametry `pOuter` i `pOwner` są przekazywane w jako `null` i funkcja ustawia podtypu projektu najbardziej zewnętrznej `IUnknown` do `pOuter`.

    2.  Następnie wywołuje środowisko `HrCreateInnerProj` funkcji z drugi identyfikator GUID typu projektu na liście. Ten identyfikator GUID odnosi się do drugiego podtypu projektu wewnętrznego przechodzenie krok po kroku kierunku projektu podstawowego w sekwencji agregacji.

    3.  `pOuter` Teraz wskazuje `IUnknown` podtypu projektu najbardziej zewnętrznej i `HrCreateInnerProj` implementacja wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> następuje wywołanie do implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metoda przekazywania w kontrolowaniu `IUnknown` podtypu projektu najbardziej zewnętrznej `pOuter`. Należących do projektu (podtypu projektu wewnętrznego) musi utworzyć jego obiekt projektu agregacji. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementacji metody przekazać wskaźnik do `IUnknown` wewnętrzny projektu, który są agregowane. Te dwie metody tworzenia obiektu agregacji, a Twoje implementacje muszą wykonać reguły agregacji COM, aby upewnić się, że podtypu projektu nie znajdą się przytrzymanie licznik odwołań do samej siebie.

    4.  `HrCreateInnerProj` Implementacja wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. W przypadku tej metody podtypu projektu działa inicjowania. Na przykład można rejestrować zdarzenia rozwiązania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5.  `HrCreateInnerProj` jest wywoływany rekursywnie, aż do osiągnięcia ostatni identyfikator GUID (podstawowy projekt) na liście. Dla każdego z tych wywołań są powtarzane czynności c do d. `pOuter` Wskazuje podtypu projektu najbardziej zewnętrznej `IUnknown` dla każdego poziomu agregacji.

## <a name="example"></a>Przykład

W poniższym przykładzie opisano proces programistyczny w przybliżony reprezentacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody jest implementowany przez środowisko. Kod jest tylko przykładowe; nie jest przeznaczone do skompilowania i usunięto sprawdzanie wszystkich błędów dla jasności.

```cpp
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

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)