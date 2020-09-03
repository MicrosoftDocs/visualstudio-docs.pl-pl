---
title: Sekwencja inicjacji podtypów projektu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707631"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sekwencja inicjowania podtypów projektów
Środowisko tworzy projekt przez wywołanie podstawowej implementacji fabryki projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . Konstrukcja podtypu projektu jest uruchamiana, gdy środowisko ustali, że lista identyfikatorów GUID typu projektu dla rozszerzenia pliku projektu nie jest pusta. Rozszerzenie pliku projektu i identyfikator GUID projektu określają, czy projekt jest [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] typem projektu lub. Na przykład rozszerzenie. vbproj i element {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identyfikują [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekt.

## <a name="environments-initialization-of-project-subtypes"></a>Inicjowanie podtypów projektu środowiska
 Poniższa procedura zawiera szczegóły sekwencji inicjalizacji dla systemu projektu agregowanego przez wiele podtypów projektu.

1. Środowisko wywołuje projekt podstawowy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> i podczas gdy projekt analizuje jego plik projektu, jest to, że lista zagregowanych identyfikatorów GUID typu projektu nie jest `null` . Projekt nie będzie kontynuował bezpośrednio tworzenia projektu.

2. Projekt wywołuje `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> usługę, aby utworzyć podtyp projektu przy użyciu implementacji metody dla środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> . W ramach tej metody środowisko wykonuje cykliczne wywołania funkcji <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> a metody, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> w trakcie przechodzenia listy typów GUID typu projektu, rozpoczynając od zewnętrznego podtypu projektu.

     Poniżej znajdują się szczegółowe informacje na temat kroków inicjalizacji.

    1. Implementacja metody dla środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> wywołuje `HrCreateInnerProj` metodę z następującą deklaracją funkcji:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Gdy ta funkcja jest wywoływana po raz pierwszy, czyli dla zewnętrznego podtypu projektu, parametry `pOuter` i są przenoszone jako, `pOwner` `null` a funkcja ustawia zewnętrzny podtyp projektu `IUnknown` na `pOuter` .

    2. Następnie funkcja wywołania środowiska `HrCreateInnerProj` z drugim typem projektu GUID na liście. Ten identyfikator GUID odnosi się do drugiego wewnętrznego podtypu projektu w kierunku projektu podstawowego w sekwencji agregacji.

    3. `pOuter`Teraz wskazuje na `IUnknown` zewnętrzny podtyp projektu i `HrCreateInnerProj` wywołuje implementację, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> po której nastąpi wywołanie implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodzie, należy przekazać kontrolę `IUnknown` nad zewnętrznym podtypem projektu `pOuter` . Projekt, którego właścicielem jest wewnętrzny, musi utworzyć w tym miejscu swój obiekt agregacji projektu. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementacji metody przekazuje się wskaźnik do `IUnknown` wewnętrznego projektu, który jest agregowany. Te dwie metody tworzą obiekt agregacji, a implementacje muszą spełniać reguły agregacji modelu COM, aby upewnić się, że podtyp projektu nie kończy się przytrzymywaniem do siebie liczby odwołań.

    4. `HrCreateInnerProj` wywołuje implementację programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . W tej metodzie, podtyp projektu wykonuje działanie inicjalizacji. Można na przykład zarejestrować zdarzenia rozwiązania w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .

    5. `HrCreateInnerProj` jest wywoływana rekursywnie do momentu osiągnięcia ostatniego identyfikatora GUID (projekt podstawowy) na liście. W przypadku każdego z tych wywołań powtarzają się kroki od c do d. `pOuter` wskazuje zewnętrzny podtyp projektu `IUnknown` dla każdego poziomu agregacji.

## <a name="example"></a>Przykład

Poniższy przykład zawiera szczegółowe informacje o procesie programistycznym w przybliżonej reprezentacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metody, która jest implementowana w środowisku. Kod jest tylko przykładem; nie jest on przeznaczony do kompilowania i wszystkie sprawdzanie błędów zostało usunięte do przejrzystości.

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
