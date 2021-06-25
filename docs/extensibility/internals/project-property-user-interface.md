---
title: Właściwość projektu Interfejs użytkownika | Microsoft Docs
description: Dowiedz się, jak podtypy projektów mogą modyfikować okno dialogowe Strony właściwości projektu dostarczone przez projekt podstawowy.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77e3554f2a3fd3b0dc1d608bb7d0a1198116a4e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903592"
---
# <a name="project-property-user-interface"></a>Interfejs użytkownika właściwości projektu

Podtyp projektu może używać elementów  w oknie dialogowym Strony właściwości projektu, ponieważ są one dostarczane przez projekt podstawowy, ukrywać lub ować kontrolki tylko do odczytu i całe strony jako dostarczone lub dodawać strony specyficzne dla podtypu projektu do okna dialogowego **Strony** właściwości.

## <a name="extending-the-project-property-dialog-box"></a>Rozszerzanie właściwości projektu, okno dialogowe

Podtyp projektu implementuje rozszerzenia automatyzacji i konfigurację projektu przeglądania obiektów. Te rozszerzenia implementują <xref:EnvDTE.IFilterProperties> interfejs, aby ukrywać konkretne właściwości lub tylko do odczytu. W **oknie dialogowym** Strony właściwości projektu podstawowego, zaimplementowanym przez projekt podstawowy, jest honorowane filtrowanie wykonywane przez rozszerzenia automatyzacji.

Proces rozszerzania okna dialogowego **Project Property (Właściwość projektu)** został opisany poniżej:

- Projekt podstawowy pobiera rozszerzenia z podtypu projektu, implementując <xref:EnvDTE80.IInternalExtenderProvider> interfejs . Przeglądanie, automatyzacja projektu i konfiguracja projektu przeglądają obiekty projektu podstawowego i implementują ten interfejs.

- Implementacja obiektu przeglądania projektu i obiektu automatyzacji projektu delegowanego do implementacji agregatora podtypu projektu (czyli dla obiektu <xref:EnvDTE80.IInternalExtenderProvider> <xref:EnvDTE80.IInternalExtenderProvider> `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu).

- Obiekt przeglądania konfiguracji projektu podstawowego implementuje również bezpośrednie przewodowanie w rozszerzeniu automatyzacji <xref:EnvDTE80.IInternalExtenderProvider> z obiektu konfiguracji podtypu projektu. Jego implementacja deleguje interfejs <xref:EnvDTE80.IInternalExtenderProvider> zaimplementowany przez agregator podtypu projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, zaimplementowany przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, również zaimplementowany przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiekt .

- Podtyp projektu może określić odpowiednie identyfikatory CATID dla różnych rozszerzalnych obiektów projektu podstawowego w czasie uruchamiania, pobierania następujących <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wartości:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Aby określić identyfikatory CATID dla zakresu projektu, podtyp projektu pobiera powyższe właściwości dla [vsitemid. Katalog](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) główny z `VSITEMID typedef` katalogu . Podtyp projektu może również chcieć kontrolować, które strony okna dialogowego Strony właściwości są wyświetlane dla projektu, zarówno zależne od konfiguracji, jak i niezależne od konfiguracji.  Niektóre podtypy projektów mogą wymagać usunięcia wbudowanych stron i dodania określonych stron podtypu projektu. Aby to umożliwić, projekt klienta zarządzanego wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodę dla następujących właściwości:

- `VSHPROPID_PropertyPagesCLSIDList` — rozdzielana średnikami lista identyfikatorów CLSID stron właściwości niezależnych od konfiguracji.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` rozdzielana średnikami lista identyfikatorów CLSID stron właściwości zależnych od konfiguracji.

Ponieważ podtyp projektu agreguje obiekt, może zastąpić definicję tych właściwości, aby kontrolować, które strony właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> są wyświetlane w oknach dialogowych.  Podtyp projektu może pobrać te właściwości z wewnętrznego projektu podstawowego, a następnie w razie potrzeby dodać lub usunąć identyfikatory CLSID.

Do nowych stron właściwości dodanych przez podtyp projektu jest dodawany obiekt przeglądania konfiguracji projektu z implementacji projektu podstawowego. Ten obiekt przeglądania konfiguracji projektu obsługuje rozszerzenia automatyzacji. Aby uzyskać więcej informacji na temat usługi AutomationExtenders, zobacz [Implementowanie i używanie rozszerzania automatyzacji.](/previous-versions/0y92k2w2(v=vs.140)) Strony właściwości zaimplementowane przez wywołanie podtypu projektu w celu pobrania własnego obiektu przeglądania konfiguracji podtypu projektu, który rozszerza obiekt <xref:EnvDTE.Project.Extender%2A> przeglądania konfiguracji projektu podstawowego.

## <a name="see-also"></a>Zobacz też

- <xref:EnvDTE.IFilterProperties>
- [Strony właściwości, okno dialogowe](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))