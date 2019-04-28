---
title: Interfejs użytkownika właściwości projektu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b54c6ba8f3daefa53f00478c1d7e4573311cfb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429161"
---
# <a name="project-property-user-interface"></a>Interfejs użytkownika właściwości projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtypu projektu można użyć elementów w projekcie **stron właściwości** okno dialogowe, ponieważ są one dostarczane przez projektu podstawowego, ukryć lub przygotowywanie kontrolek tylko do odczytu i całe strony dostarczony lub dodać strony specyficzne dla podtypu projektu do **Stron właściwości** okno dialogowe.  
  
## <a name="extending-the-project-property-dialog-box"></a>Rozszerzanie okno dialogowe właściwości projektu  
 Podtypu projektu implementuje urządzeń Extender automatyzacji i obiekty przeglądania konfiguracji projektu. Implementacji tych rozszerzeń <xref:EnvDTE.IFilterProperties> interfejsu, aby wprowadzić szczególne właściwości ukryte lub tylko do odczytu. **Stron właściwości** okno dialogowe projektu podstawowego, implementowany przez projektu podstawowego honoruje, filtrowanie, wykonywane przez automatyzacji urządzeń Extender.  
  
 Proces rozszerzania **właściwość projektu** okno dialogowe jest przedstawiona poniżej:  
  
- Podstawowy projekt pobiera rozszerzeń z podtypu projektu poprzez implementację <xref:EnvDTE80.IInternalExtenderProvider> interfejsu. Przeglądanie, automatyzacji projektu i projektu konfiguracji przeglądania obiektów projektu podstawowego wszystkich implementować ten interfejs.  
  
- Implementacja <xref:EnvDTE80.IInternalExtenderProvider> dla obiektu przeglądania projektu i obiektu automatyzacji projektu delegować do <xref:EnvDTE80.IInternalExtenderProvider> implementacji agregatora podtypu projektu (oznacza to, że ich `QueryInterface` dla <xref:EnvDTE80.IInternalExtenderProvider> na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt projektu).  
  
- Implementuje również obiekt przeglądania konfiguracji projektu podstawowego <xref:EnvDTE80.IInternalExtenderProvider> celu bezpośrednio podłączenia w Extender automatyzacji z obiekt konfiguracji podtypu projektu. Jego implementacja deleguje do <xref:EnvDTE80.IInternalExtenderProvider> interfejs implementowany przez agregator podtypu projektu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementowane przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, również implementowany przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiektu.  
  
- Podtypu projektu można określić odpowiednich identyfikatorów CatID dla różnych obiektów rozszerzalnej podstawowego projektu w czasie wykonywania, pobierając następujące <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wartości:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  Aby określić identyfikatorów CatID zakresu projektu, podtypu projektu pobiera powyżej właściwości <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> z `VSITEMID``typedef`. Podtypu projektu może być również kontrolować, które **strony właściwości** okna dialogowego pola strony są wyświetlane dla projektu, niezależnie od konfiguracji i zależne od konfiguracji. Niektóre podtypy projektów może być konieczne Usuń wbudowane strony i Dodaj określonych stron podtypu projektu. Aby włączyć to wywoływanych w projekcie zarządzanego klienta <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metoda następujących właściwości:  
  
- `VSHPROPID_PropertyPagesCLSIDList` — rozdzieloną średnikami listę CLSID strony właściwości niezależne od konfiguracji.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` Rozdzielana średnikami lista CLSID strony właściwości zależne od konfiguracji.  
  
  Ponieważ projekt podtypu agregacje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu, można zastąpić, definicja tych właściwości, aby kontrolować, które **stron właściwości** okna dialogowe są wyświetlane. Podtypu projektu można pobrać te właściwości z wewnętrznego podstawowego projektu i następnie dodawać i usuwać CLSID zgodnie z potrzebami.  
  
  Nowe strony właściwości dodane przez podtypu projektu są przekazywane obiekt przeglądania konfiguracji projektu z projektu podstawowego wdrożenia. Ten obiekt przeglądania konfiguracji projektu obsługuje automatyzacji urządzeń Extender. Aby uzyskać więcej informacji na temat AutomationExtenders, zobacz [wdrażania i przy użyciu automatyzacji urządzeń Extender](http://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356). Strony właściwości implementowane przez wywołanie podtypu projektu <xref:EnvDTE.Project.Extender%2A> można pobrać ich własnych projektów podtyp konfiguracji przeglądania obiekt, który rozszerza obiekt przeglądania konfiguracji projektu podstawowego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:EnvDTE.IFilterProperties>   
 [Okno dialogowe strony właściwości](http://msdn.microsoft.com/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
