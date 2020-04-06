---
title: Interfejs użytkownika właściwości projektu | Dokumenty firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706396"
---
# <a name="project-property-user-interface"></a>Interfejs użytkownika właściwości projektu

Podtyp projektu może używać elementów w oknie dialogowym **Strony właściwości** projektu, ponieważ są one dostarczane przez projekt podstawowy, ukrywać lub tworzyć formanty tylko do odczytu i całe strony, jak podano, lub dodawać strony specyficzne dla podtypu projektu do okna dialogowego **Strony właściwości.**

## <a name="extending-the-project-property-dialog-box"></a>Rozszerzanie okna dialogowego właściwości projektu

Podtyp projektu implementuje rozszerzenia automatyzacji i przeglądanie obiektów konfiguracji projektu. Te extendery <xref:EnvDTE.IFilterProperties> implementują interfejs, aby poszczególne właściwości były ukryte lub tylko do odczytu. Okno dialogowe **Strony właściwości** projektu podstawowego, realizowane przez projekt podstawowy, honoruje filtrowanie wykonywane przez moduły extender automatyzacji.

Proces rozszerzania okna dialogowego **właściwości projektu** opisano poniżej:

- Projekt podstawowy pobiera extendery z podtypu projektu, <xref:EnvDTE80.IInternalExtenderProvider> implementując interfejs. Przeglądanie, automatyzacja projektu i konfiguracja projektu przeglądać obiekty projektu podstawowego wszystkie implementują ten interfejs.

- Implementacja <xref:EnvDTE80.IInternalExtenderProvider> dla obiektu przeglądania projektu i delegata obiektu <xref:EnvDTE80.IInternalExtenderProvider> automatyzacji projektu do implementacji agregatora podtypu projektu (czyli `QueryInterface` dla <xref:EnvDTE80.IInternalExtenderProvider> obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu).

- Obiekt przeglądania konfiguracji projektu podstawowego <xref:EnvDTE80.IInternalExtenderProvider> implementuje również do bezpośredniego przewodach w rozszerzeniu automatyzacji z obiektu konfiguracji podtypu projektu. Jego implementacja jest <xref:EnvDTE80.IInternalExtenderProvider> delegatami do interfejsu zaimplementowanego przez agregator podtypu projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, zaimplementowane przez obiekt przeglądania <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> konfiguracji projektu, zwraca obiekt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, również zaimplementowane przez obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> przeglądania konfiguracji projektu, zwraca obiekt.

- Podtyp projektu może określić odpowiednie identyfikatory CATID dla różnych obiektów rozszerzalnych <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> projektu podstawowego w czasie wykonywania, pobierając następujące wartości:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Aby określić catids dla zakresu projektu, podtyp projektu pobiera powyższe właściwości [vsitemid. Korzeń](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef`z . Podtyp projektu może również chcieć kontrolować, które strony okna dialogowego **Strony właściwości** są wyświetlane dla projektu, zarówno zależne od konfiguracji, jak i niezależne od konfiguracji. Niektóre podtypy projektu mogą wymagać usunięcia wbudowanych stron i dodania stron określonych podtyp projektu. Aby włączyć tę funkcję, projekt zarządzanego klienta wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodę dla następujących właściwości:

- `VSHPROPID_PropertyPagesCLSIDList`— lista rozdzielanych średnikami clsidów stron właściwości niezależnych od konfiguracji.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`lista rozdzielanych średnikami identyfikatorów CLSID stron właściwości zależnych od konfiguracji.

Ponieważ podtyp projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> agreguje obiekt, może zastąpić definicję tych właściwości, aby kontrolować, które okna dialogowe **strony właściwości** są wyświetlane. Podtyp projektu można pobrać te właściwości z projektu podstawowego wewnętrznego, a następnie dodać lub usunąć CLSIDs w razie potrzeby.

Nowe strony właściwości dodane przez podtyp projektu są przekazywane obiekt przeglądania konfiguracji projektu z implementacji projektu podstawowego. Ten obiekt przeglądania konfiguracji projektu obsługuje rozszerzenia automatyzacji. Aby uzyskać więcej informacji na temat AutomationExtenders, zobacz [Implementowanie i używanie wzmacniaczy automatyzacji](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Strony właściwości zaimplementowane przez <xref:EnvDTE.Project.Extender%2A> wywołanie podtypu projektu w celu pobrania własnego obiektu przeglądania konfiguracji podtypu projektu, który rozszerza obiekt przeglądania konfiguracji projektu podstawowego.

## <a name="see-also"></a>Zobacz też

- <xref:EnvDTE.IFilterProperties>
- [Okno dialogowe Strony właściwości](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
