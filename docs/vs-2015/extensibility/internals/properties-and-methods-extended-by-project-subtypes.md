---
title: Właściwości i metody rozszerzane przez podtypy projektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f74f1f4a88fb01e09b30e7987f1bcec1d450571a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765127"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Właściwości i metody rozszerzane przez podtypy projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projekt ma wiele możliwości do wywierania wpływu na zachowanie projektu, ponieważ jest konstruowany jako agregatora projektu podstawowego. Ta sekcja zawiera podsumowanie niektórych funkcji, które mogą być rozszerzony lub modyfikowane przez podtypy projektów.  
  
## <a name="features-gained-by-aggregation"></a>Funkcje uzyskiwane dzięki agregacji  
 W poniższej tabeli przedstawiono wiele metod, które podtypy projektów do zastąpienia w podstawowej projektów agregacji.  
  
|Metody zastąpione agregacji|Podtypu projektu|  
|---------------------------------------|---------------------|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Włącza podtypu projektu<br /><br /> -Zmień podpis i ikona węzeł projektu.<br />-Całkowicie zastąpić projektu `Browse` obiektu.<br />-Kontrolować, czy można zmienić nazwy projektu.<br />-Kolejność sortowania control.<br />-Kontekst użytkownika control dynamiczna Pomoc.|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Pozwala kontrolować, jakie kontekstowych usługi podano projektanci i edytory podtypu projektu.|  
|Z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Włącza podtypu projektu<br /><br /> -Uczestniczyć w routingu poleceń polecenia projektu.<br />— Dodać, usunąć lub wyłączyć polecenia otoczenia projektu i aktywne polecenia Eksploratora rozwiązań.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Włącza podtypu projektu do filtrowania, użytkownik zobaczy w **Dodaj nowy element** okno dialogowe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Włącza podtypu projektu<br /><br /> -Określ domyślny generator danego rozszerzenia pliku.<br />— Mapowanie nazwa generatora można odczytać ludzi do obiektu COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Właściwości używanych przez podtypy projektów  
 System projektu środowiska i podstawowej, można użyć właściwości z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> wyliczenia szczegółowo opisane w poniższej tabeli umożliwiające podtypem projektu do kontrolowania różnych funkcji systemu projektu.  
  
|Właściwość VSHPROPID|Podtypu projektu|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Umożliwia podtypu projektu kontrolować zawartość **elementu Dodawanie** okno dialogowe. Podtypu projektu można podać nową specyfikację katalogów szablonu, Dodaj nowe rodzaje elementów, Usuń istniejące elementy i reorganizować podzbiór elementów projektu podstawowego **elementu Dodawanie** okno dialogowe.|  
|`PropertyPagesCLSIDList`|Umożliwia podtypu projektu, dodawanie i usuwanie stron właściwości niezależne od konfiguracji.|  
|`CfgPropertyPagesCLSIDList`|Umożliwia podtypu projektu, dodawanie i usuwanie stron właściwości zależne od konfiguracji.|  
|`ExtObjectCATID`|Umożliwia zapewnienie urządzenia Extender automatyzacji projektu lub projektu obiektów elementów znając Identyfikator CATID rozszerzeń podtypem projektu. Na przykład podtypu projektu można podać niestandardowy `Project.Extender("<subtype>")` obiektu.|  
|`BrowseObjectCATID`|Umożliwia podtypem projektu umożliwia rozszerzenie automatyzacji dla `Browse` obiektu znając Identyfikator CATID rozszerzeń. Na przykład podtypu projektu można dodać dodatkowe właściwości, aby <xref:EnvDTE.Project.Properties%2A> kolekcji.|  
|`CfgBrowseObjectCATID`|Umożliwia podtypem projektu do zapewnienia urządzenia Extender automatyzacji obiekt przeglądania konfiguracji projektu. Na przykład podtypu projektu można dodać dodatkowe właściwości, aby <xref:EnvDTE.Configuration.Properties%2A> kolekcji.|  
|`CfgExtObjectCATID`|Umożliwia podtypem projektu zapewnienie urządzenia Extender automatyzacji dla obiektu konfiguracji.|  
|`DefaultPlatformName`|Umożliwia podtypem projektu można określić nazwy platformy dla obiektów konfiguracji projektu.|  
  
 Podstawowy projekt udostępnia domyślną implementację interfejsu powyżej właściwości. Projektu podstawowego pobiera je przez wywołanie metody `QueryInterface` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> na podtypem projektu najbardziej zewnętrznego, dzięki czemu podtypu projektu do przesłonięcia implementację właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)

