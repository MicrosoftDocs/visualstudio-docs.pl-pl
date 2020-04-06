---
title: Udostępnianie obiektów projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708468"
---
# <a name="expose-project-objects"></a>Udostępnianie obiektów projektu

Niestandardowe typy projektów można zapewnić obiekty automatyzacji w celu umożliwienia dostępu do projektu za pomocą interfejsów automatyzacji. Każdy typ projektu ma zapewnić <xref:EnvDTE.Project> standardowy obiekt automatyzacji, który jest dostępny z <xref:EnvDTE.Solution>, który zawiera kolekcję wszystkich projektów, które są otwarte w IDE. Oczekuje się, że każdy element w <xref:EnvDTE.ProjectItem> projekcie zostanie `Project.ProjectItems`ujawniony przez obiekt, do którego dostęp ma . Oprócz tych standardowych obiektów automatyzacji, projekty można wybrać do zaoferowania obiektów automatyzacji specyficzne dla projektu.

Można utworzyć niestandardowe obiekty automatyzacji na poziomie głównym, do których `DTE.<customObjectName>` można `DTE.GetObject("<customObjectName>")`uzyskać dostęp z późnego powiązanego obiektu DTE za pomocą obiektu DTE lub . Na przykład visual C++ tworzy kolekcję projektu specyficzne dla projektu C++ o `DTE.VCProjects` nazwie `DTE.GetObject("VCProjects")` *VCProjects,* do których można uzyskać dostęp za pomocą lub . Można również utworzyć `Project.Object`program , który jest unikatowy dla typu `Project.CodeModel`projektu, , który może być `ProjectItem`wyszukiwany `ProjectItem.Object` dla `ProjectItem.FileCodeModel`jego najbardziej pochodnego obiektu, oraz , który udostępnia i .

Jest to wspólna konwencja dla projektów, aby udostępnić niestandardowe, kolekcji projektu specyficzne dla projektu. Na przykład [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tworzy kolekcję projektu specyficznego dla języka `DTE.VCProjects` `DTE.GetObject("VCProjects")`C++, do której można uzyskać dostęp za pomocą programu lub . Można również utworzyć `Project.Object`program , który jest unikatowy dla typu `Project.CodeModel`projektu, , który może `ProjectItem`być wyszukiwany `ProjectItem.Object`dla `ProjectItem.FileCodeModel`jego najbardziej pochodnego obiektu, , który udostępnia , i .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Aby przyczynić się do vspackage specyficzne obiektu dla projektu

1. Dodaj odpowiednie klucze do pliku *pkgdef* pliku vspackage.

     Oto na przykład ustawienia *pkgdef* dla projektu języka C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Zaimplementuj kod w metodzie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> jak w poniższym przykładzie.

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

     W kodzie `g_wszAutomationProjects` jest nazwa kolekcji projektu. Metoda `GetAutomationProjects` tworzy obiekt, który `Projects` implementuje interfejs `IDispatch` i zwraca wskaźnik do obiektu wywołującego, jak pokazano w poniższym przykładzie kodu.

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

     Wybierz unikatową nazwę obiektu automatyzacji. Konflikty nazw są nieprzewidywalne, a kolizje powodują, że nazwa obiektu powodująca konflikt jest dowolnie wyrzucana, jeśli wiele typów projektów używa tej samej nazwy. Należy dołączyć nazwę firmy lub jakiś unikatowy aspekt jego nazwy produktu w nazwie obiektu automatyzacji.

     Obiekt `Projects` kolekcji niestandardowej jest punktem wejścia wygody dla pozostałej części modelu automatyzacji projektu. Obiekt projektu jest również <xref:EnvDTE.Solution> dostępny z kolekcji projektu. Po utworzeniu odpowiedniego kodu i wpisów rejestru, `Projects` które zapewniają konsumentom obiekty kolekcji, implementacja musi dostarczyć pozostałe obiekty standardowe dla modelu projektu. Aby uzyskać więcej informacji, zobacz [Modelowanie projektu](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
