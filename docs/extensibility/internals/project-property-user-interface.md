---
title: Interfejs użytkownika właściwości projektu | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f341a0825c4fcacc41fc01b29c6d65882fa500d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335301"
---
# <a name="project-property-user-interface"></a>Interfejs użytkownika właściwości projektu

Podtypu projektu można użyć elementów w projekcie **stron właściwości** okno dialogowe, ponieważ są one dostarczane przez projektu podstawowego, ukryć lub przygotowywanie kontrolek tylko do odczytu i całe strony dostarczony lub dodać strony specyficzne dla podtypu projektu do **Stron właściwości** okno dialogowe.

## <a name="extending-the-project-property-dialog-box"></a>Rozszerzanie okno dialogowe właściwości projektu

Podtypu projektu implementuje urządzeń Extender automatyzacji i obiekty przeglądania konfiguracji projektu. Implementacji tych rozszerzeń <xref:EnvDTE.IFilterProperties> interfejsu, aby wprowadzić szczególne właściwości ukryte lub tylko do odczytu. **Stron właściwości** okno dialogowe projektu podstawowego, implementowany przez projektu podstawowego honoruje, filtrowanie, wykonywane przez automatyzacji urządzeń Extender.

Proces rozszerzania **właściwość projektu** okno dialogowe jest przedstawiona poniżej:

-   Podstawowy projekt pobiera rozszerzeń z podtypu projektu poprzez implementację <xref:EnvDTE80.IInternalExtenderProvider> interfejsu. Przeglądanie, automatyzacji projektu i projektu konfiguracji przeglądania obiektów projektu podstawowego wszystkich implementować ten interfejs.

-   Implementacja <xref:EnvDTE80.IInternalExtenderProvider> dla obiektu przeglądania projektu i obiektu automatyzacji projektu delegować do <xref:EnvDTE80.IInternalExtenderProvider> implementacji agregatora podtypu projektu (oznacza to, że ich `QueryInterface` dla <xref:EnvDTE80.IInternalExtenderProvider> na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt projektu).

-   Implementuje również obiekt przeglądania konfiguracji projektu podstawowego <xref:EnvDTE80.IInternalExtenderProvider> celu bezpośrednio podłączenia w Extender automatyzacji z obiekt konfiguracji podtypu projektu. Jego implementacja deleguje do <xref:EnvDTE80.IInternalExtenderProvider> interfejs implementowany przez agregator podtypu projektu.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementowane przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, również implementowany przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiektu.

-   Podtypu projektu można określić odpowiednich identyfikatorów CatID dla różnych obiektów rozszerzalnej podstawowego projektu w czasie wykonywania, pobierając następujące <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wartości:

    - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

    - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

    - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Aby określić identyfikatorów CatID zakresu projektu, podtypu projektu pobiera powyżej właściwości [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) z `VSITEMID typedef`. Podtypu projektu może być również kontrolować, które **strony właściwości** okna dialogowego pola strony są wyświetlane dla projektu, niezależnie od konfiguracji i zależne od konfiguracji. Niektóre podtypy projektów może być konieczne Usuń wbudowane strony i Dodaj określonych stron podtypu projektu. Aby włączyć to wywoływanych w projekcie zarządzanego klienta <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metoda następujących właściwości:

-   `VSHPROPID_PropertyPagesCLSIDList` — rozdzieloną średnikami listę CLSID strony właściwości niezależne od konfiguracji.

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` Rozdzielana średnikami lista CLSID strony właściwości zależne od konfiguracji.

Ponieważ projekt podtypu agregacje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu, można zastąpić, definicja tych właściwości, aby kontrolować, które **stron właściwości** okna dialogowe są wyświetlane. Podtypu projektu można pobrać te właściwości z wewnętrznego podstawowego projektu i następnie dodawać i usuwać CLSID zgodnie z potrzebami.

Nowe strony właściwości dodane przez podtypu projektu są przekazywane obiekt przeglądania konfiguracji projektu z projektu podstawowego wdrożenia. Ten obiekt przeglądania konfiguracji projektu obsługuje automatyzacji urządzeń Extender. Aby uzyskać więcej informacji na temat AutomationExtenders, zobacz [wdrażania i przy użyciu automatyzacji urządzeń Extender](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Strony właściwości implementowane przez wywołanie podtypu projektu <xref:EnvDTE.Project.Extender%2A> można pobrać ich własnych projektów podtyp konfiguracji przeglądania obiekt, który rozszerza obiekt przeglądania konfiguracji projektu podstawowego.

## <a name="see-also"></a>Zobacz także

- <xref:EnvDTE.IFilterProperties>
- [Okno dialogowe strony właściwości](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))