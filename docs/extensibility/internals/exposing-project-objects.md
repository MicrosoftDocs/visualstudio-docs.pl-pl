---
title: Udostępnianie obiektów projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed19972fb2f71104357977554984ae43f886c950
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861185"
---
# <a name="expose-project-objects"></a>Udostępnianie obiektów projektu

Typy projektów niestandardowych można podać obiektów automatyzacji, aby zezwolić na dostęp do projektu przy użyciu interfejsów automatyzacji. Każdy typ projektu powinien zapewniać standard <xref:EnvDTE.Project> obiektu automatyzacji, który jest dostępny z <xref:EnvDTE.Solution>, który zawiera zbiór wszystkich projektów, które są otwarte w środowisku IDE. Każdy element w projekcie powinien być udostępniane przez <xref:EnvDTE.ProjectItem> obiektu uzyskuje się z czasem `Project.ProjectItems`. Oprócz tych obiektów automatyzacji w wersji standard projektów można zaoferować obiektów automatyzacji specyficznych dla projektu.

Możesz utworzyć niestandardowe poziomu głównego obiektów automatyzacji, które mogą uzyskać dostęp z późnym wiązaniem z głównego DTE obiektu przy użyciu `DTE.<customObjectName>` lub `DTE.GetObject("<customObjectName>")`. Na przykład Visual C++ Tworzy kolekcję projektu specyficznego dla projektu C++ o nazwie *VCProjects* , uzyskiwać dostęp za pomocą `DTE.VCProjects` lub `DTE.GetObject("VCProjects")`. Można również utworzyć `Project.Object`, który jest unikatowy dla typu projektu `Project.CodeModel`, może być odpytywany dla swoich najbardziej pochodnego obiektu i `ProjectItem`, który ujawnia `ProjectItem.Object` i `ProjectItem.FileCodeModel`.

Jest typową Konwencją projekty do udostępnienia jako zbiór projektów niestandardowych, specyficzne dla projektu. Na przykład [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tworzy kolekcję określonego projektu C++, który można następnie uzyskać dostęp za pomocą `DTE.VCProjects` lub `DTE.GetObject("VCProjects")`. Można również utworzyć `Project.Object`, który jest unikatowy dla typu projektu `Project.CodeModel`, może być odpytywany dla swoich najbardziej pochodnego obiektu `ProjectItem`, który ujawnia `ProjectItem.Object`, a `ProjectItem.FileCodeModel`.

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Aby współtworzyć obiekt pakietu VSPackage specyficzne dla projektu

1. Dodaj odpowiednie klucze, aby *.pkgdef* plik z pakietu VSPackage.

     Na przykład Oto *.pkgdef* ustawienia dla projektów języka C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Wdrożyć kod w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metody, jak w poniższym przykładzie.

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

     Wybierz unikatową nazwę dla obiektu automatyzacji. Konflikty nazw są nieprzewidywalne i kolizji powodują konflikt nazwy obiektów arbitralnie zostanie wygenerowany użycie tej samej nazwie, wiele typów projektów. Należy dołączyć nazwę firmy lub niektóre unikatowe aspekty jego nazwę produktu, nazwę obiektu automatyzacji.

     Niestandardowy `Projects` obiekt kolekcji jest punktem wejścia jako udogodnienie dla pozostałej części projektu modelu automatyzacji. Obiekt projektu jest także dostępny z <xref:EnvDTE.Solution> kolekcji projektów. Po utworzeniu odpowiedni kod i wpisy rejestru, które zapewniają klientom `Projects` obiekty kolekcji implementacji należy podać pozostałe standardowe obiekty modelu projektu. Aby uzyskać więcej informacji, zobacz [projektu modelowania](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
