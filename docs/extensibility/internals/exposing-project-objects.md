---
title: Udostępnianie obiektów projektu | Microsoft Docs
description: Dowiedz się, jak uwidocznić obiekty dla niestandardowych typów projektów w programie Visual Studio udostępniając obiekty automatyzacji, które umożliwiają dostęp do projektu przy użyciu interfejsów automatyzacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3e89b4c80d64bedb77e68c648ba993794f8b658
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898295"
---
# <a name="expose-project-objects"></a>Uwidocznij obiekty projektu

Niestandardowe typy projektów mogą zapewniać obiekty automatyzacji w celu umożliwienia dostępu do projektu przy użyciu interfejsów automatyzacji. Każdy typ projektu powinien zapewniać standardowy obiekt automatyzacji dostępny z , który zawiera kolekcję wszystkich projektów, które <xref:EnvDTE.Project> <xref:EnvDTE.Solution> są otwarte w idee . Oczekuje się, że każdy element w projekcie zostanie ujawniony przez <xref:EnvDTE.ProjectItem> obiekt, do którego uzyskano dostęp za pomocą elementu `Project.ProjectItems` . Oprócz tych standardowych obiektów automatyzacji projekty mogą oferować obiekty automatyzacji specyficzne dla projektu.

Możesz utworzyć niestandardowe obiekty automatyzacji na poziomie głównym, do których można uzyskać dostęp z głównego obiektu DTE z późnym wiązaniem przy użyciu `DTE.<customObjectName>` lub `DTE.GetObject("<customObjectName>")` . Na przykład Visual C++ kolekcję projektów specyficzną dla projektu języka C++ o nazwie *VCProjects,* do których można uzyskać dostęp przy użyciu lub `DTE.VCProjects` `DTE.GetObject("VCProjects")` . Można również utworzyć obiekt , który jest unikatowy dla typu projektu, obiekt , do którego można tworzyć zapytania dotyczące jego najbardziej pochodnego obiektu, oraz obiekt , który uwidacznia obiekt `Project.Object` `Project.CodeModel` i `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .

Jest to powszechna konwencja, w przypadku których projekty uwidoczniają niestandardową kolekcję projektów specyficzną dla projektu. Na przykład program tworzy kolekcję projektów specyficzną dla języka [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] C++, do których można uzyskać dostęp przy użyciu lub `DTE.VCProjects` `DTE.GetObject("VCProjects")` . Można również utworzyć obiekt , który jest unikatowy dla typu projektu, , który może być wyszukiwany dla jego obiektu najbardziej pochodnego, obiekt , który uwidacznia `Project.Object` `Project.CodeModel` obiekt i `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Aby współtwokować obiekt specyficzny dla pakietów VSPackage dla projektu

1. Dodaj odpowiednie klucze do pliku *pkgdef* twojego vspackage.

     Na przykład poniżej znajdują się *ustawienia PKGDEF* dla projektu języka C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Zaim implementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> kod w metodzie , jak w poniższym przykładzie.

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

     W kodzie `g_wszAutomationProjects` jest nazwą kolekcji projektu. Metoda tworzy obiekt, który implementuje interfejs i zwraca wskaźnik do obiektu wywołującego, jak `GetAutomationProjects` `Projects` `IDispatch` pokazano w poniższym przykładzie kodu.

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

     Wybierz unikatową nazwę obiektu automatyzacji. Konflikty nazw są nieprzewidywalne, a kolizje powodują, że nazwa obiektu powodującego konflikt jest dowolnie zgłaszana, jeśli wiele typów projektów używa tej samej nazwy. W nazwie obiektu automatyzacji należy uwzględnić nazwę firmy lub unikatowy aspekt jej nazwy produktu.

     Niestandardowy obiekt kolekcji jest wygodnym punktem `Projects` wejścia dla pozostałej części modelu automatyzacji projektu. Obiekt projektu jest również dostępny z <xref:EnvDTE.Solution> kolekcji projektu. Po utworzeniu odpowiedniego kodu i wpisów rejestru, które zapewniają użytkownikom obiekty kolekcji, implementacja musi zapewnić pozostałe obiekty standardowe `Projects` dla modelu projektu. Aby uzyskać więcej informacji, zobacz [Modelowanie projektu](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
