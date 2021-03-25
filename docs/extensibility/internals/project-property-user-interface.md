---
title: Interfejs użytkownika właściwości projektu | Microsoft Docs
description: Dowiedz się, jak podtypy projektu mogą modyfikować okno dialogowe strony właściwości projektu, zgodnie z danymi projektu podstawowego.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
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
ms.openlocfilehash: 051c373b85eff4483012dec5b264fa09fe7d962e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064478"
---
# <a name="project-property-user-interface"></a>Interfejs użytkownika właściwości projektu

Podtyp projektu może korzystać z elementów w oknie dialogowym **strony właściwości** projektu, ponieważ są one dostarczane przez projekt podstawowy, ukrywać lub tworzyć formanty tylko do odczytu oraz całe strony jako dostarczone lub dodać strony specyficzne dla podtypów projektu do okna dialogowego **strony właściwości** .

## <a name="extending-the-project-property-dialog-box"></a>Rozszerzanie właściwości projektu — okno dialogowe

Podtyp projektu implementuje rozszerzalności automatyzacji i obiekty przeglądania konfiguracji projektu. Te rozszerzalności implementują <xref:EnvDTE.IFilterProperties> interfejs, aby zapewnić, że określone właściwości są ukryte lub tylko do odczytu. Okno dialogowe **strony właściwości** projektu podstawowego, zaimplementowane przez projekt podstawowy, ma wpływ na filtrowanie wykonywane przez rozszerzalności automatyzacji.

Proces rozszerzania **właściwości projektu** okno dialogowe znajduje się poniżej:

- Projekt podstawowy pobiera rozszerzalności z podtypu projektu przez implementację <xref:EnvDTE80.IInternalExtenderProvider> interfejsu. Obiekty przeglądające, Automatyzacja projektów i konfiguracja projektu projektu podstawowego wszystkie implementują ten interfejs.

- Implementacja <xref:EnvDTE80.IInternalExtenderProvider> dla obiektu przeglądanie projektu i delegat obiektu automatyzacji projektu do <xref:EnvDTE80.IInternalExtenderProvider> implementacji agregatora podtypu projektu (czyli `QueryInterface` dla <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu projektu).

- Obiekt przeglądarki konfiguracji projektu podstawowego jest również wdrażany <xref:EnvDTE80.IInternalExtenderProvider> bezpośrednio w ramach rozszerzania automatyzacji z obiektu konfiguracji podtypu projektu. Jego implementacja deleguje do <xref:EnvDTE80.IInternalExtenderProvider> interfejsu zaimplementowanego przez agregator podtypów projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementowane przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, również zaimplementowane przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiekt.

- Podtyp projektu może ustalić odpowiednie CATID dla różnych rozszerzalnych obiektów projektu podstawowego w czasie wykonywania przez pobranie następujących <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wartości:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Aby określić CATID dla zakresu projektu, podtyp projektu pobiera powyższe właściwości dla [VSITEMID. Katalog główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) z `VSITEMID typedef` . Podtyp projektu może również chcieć kontrolować, które strony okna dialogowego strony **Właściwości** są wyświetlane dla projektu, zależne od konfiguracji i konfiguracji. Niektóre podtypy projektu mogą wymagać usunięcia wbudowanych stron i dodania określonych podtypów projektu. Aby to umożliwić, projekt zarządzanego klienta wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodę dla następujących właściwości:

- `VSHPROPID_PropertyPagesCLSIDList` — rozdzielana średnikami lista identyfikatorów CLSID niezależnych od konfiguracji stron właściwości.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` rozdzielana średnikami lista identyfikatorów CLSID stron właściwości zależnych od konfiguracji.

Ponieważ podtyp projektu agreguje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt, może przesłonić definicję tych właściwości, aby określić, które okna dialogowe **strony właściwości** są wyświetlane. Podtyp projektu może pobrać te właściwości z wewnętrznego projektu bazowego, a następnie dodać lub usunąć identyfikatory CLSID stosownie do potrzeb.

Nowe strony właściwości dodane przez podtyp projektu są przekazywane do obiektu przeglądania konfiguracji projektu z podstawowej implementacji projektu. Ten obiekt przeglądania konfiguracji projektu obsługuje rozszerzalności automatyzacji. Aby uzyskać więcej informacji na temat AutomationExtenders, zobacz [implementowanie i korzystanie z rozszerzeń automatyzacji](/previous-versions/0y92k2w2(v=vs.140)). Strony właściwości zaimplementowane przez wywołanie podtypu projektu <xref:EnvDTE.Project.Extender%2A> w celu pobrania własnego obiektu przeglądania konfiguracji podtypu projektu, który rozszerza obiekt przeglądania konfiguracji projektu podstawowego.

## <a name="see-also"></a>Zobacz też

- <xref:EnvDTE.IFilterProperties>
- [Okno dialogowe strony właściwości](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))