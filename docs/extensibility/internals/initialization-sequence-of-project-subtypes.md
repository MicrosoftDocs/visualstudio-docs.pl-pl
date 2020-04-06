---
title: Sekwencja inicjowania podtypów projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707631"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sekwencja inicjowania podtypów projektów
Środowisko konstruuje projekt, wywołując wdrożenie fabryki <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>projektu podstawowego . Budowa podtypu projektu rozpoczyna się, gdy środowisko określa, że lista GUID typu projektu dla rozszerzenia pliku projektu nie jest pusta. Rozszerzenie pliku projektu i identyfikator GUID projektu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] określają, czy projekt jest typem projektu czy projektem. Na przykład rozszerzenie .vbproj i {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identyfikują [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekt.

## <a name="environments-initialization-of-project-subtypes"></a>Inicjowanie podtypów projektu w środowisku
 Poniższa procedura zawiera szczegółowe informacje o sekwencji inicjowania dla systemu projektu agregowanego przez wiele podtypów projektu.

1. Środowisko wywołuje projekt podstawowy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, a podczas gdy projekt analizuje jego plik projektu odkrywa, że lista `null`identyfikatorów GUID typu projektu agregowanych nie jest . Projekt przestaje bezpośrednio tworzyć swój projekt.

2. Projekt wzywa `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> usługi do utworzenia podtypu projektu przy <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> użyciu środowiska implementacji metody. W ramach tej metody środowisko sprawia, że cykliczne <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> wywołania funkcji do implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, i metody podczas przechodzenia listy identyfikatorów GUID typu projektu, począwszy od najbardziej zewnętrznego podtypu projektu.

     Poniżej przedstawiono szczegółowe kroki inicjowania.

    1. Implementacja środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody wywołuje metodę `HrCreateInnerProj` z następującą deklaracją funkcji:

         \<Posiadacz>0</CodeContentPlaceHolder>

         Gdy ta funkcja jest wywoływana po raz pierwszy, czyli dla najbardziej `pOuter` `pOwner` zewnętrznego podtypu projektu, parametry i są przekazywane w as `null` i funkcja ustawia najbardziej zewnętrzny podtyp `IUnknown` projektu na `pOuter`.

    2. Następnie środowisko `HrCreateInnerProj` wywołuje funkcję z drugim typem guid projektu na liście. Ten identyfikator GUID odpowiada drugi podtyp projektu wewnętrznego stepping w kierunku projektu podstawowego w sekwencji agregacji.

    3. Jest `pOuter` teraz wskazując na `IUnknown` najbardziej zewnętrzny podtyp `HrCreateInnerProj` projektu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> wywołuje implementację następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>wywołanie implementacji . W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodzie należy `IUnknown` przejść w kontrolowaniu `pOuter`podtypu projektu najbardziej zewnętrznego, . Posiadany projekt (podtyp projektu wewnętrznego) musi utworzyć w tym miejscu swój obiekt projektu agregowanego. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementacji metody można przekazać `IUnknown` w wskaźniku do projektu wewnętrznego, który jest agregowany. Te dwie metody tworzą obiekt agregacji, a implementacje muszą być zgodne z regułami agregacji COM, aby upewnić się, że podtyp projektu nie zawiera liczby odwołań do siebie.

    4. `HrCreateInnerProj`nazywa wdrożenie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. W tej metodzie podtyp projektu wykonuje swoją pracę inicjowania. Zdarzenia rozwiązania można na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>zarejestrować w pliku .

    5. `HrCreateInnerProj`jest nazywany rekursywnie do momentu osiągnięcia ostatniego identyfikatora GUID (projektu podstawowego) na liście. Dla każdego z tych wywołań kroki, od c do d, są powtarzane. `pOuter`wskazuje najbardziej zewnętrzny podtyp `IUnknown` projektu dla każdego poziomu agregacji.

## <a name="example"></a>Przykład

Poniższy przykład szczegółowo proces programowy w przybliżonej reprezentacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody, jak jest zaimplementowana przez środowisko. Kod jest tylko przykładem; nie jest przeznaczony do kompilacji, a wszystkie sprawdzanie błędów zostało usunięte dla jasności.

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
