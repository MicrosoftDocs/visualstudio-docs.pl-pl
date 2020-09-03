---
title: Właściwości i metody rozszerzone przez podtypy projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20892d50afc529b410e8e0bdfa3c4b52fdc1b9b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154124"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Właściwości i metody rozszerzane przez podtypy projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu ma wiele mocy do wpływu na zachowanie projektu, ponieważ jest skonstruowany jako agregator projektu podstawowego. Ta sekcja zawiera podsumowanie niektórych funkcji, które można rozszerzyć lub zmodyfikować według podtypów projektu.  
  
## <a name="features-gained-by-aggregation"></a>Funkcje uzyskane przez agregację  
 Poniższa tabela zawiera podsumowanie wielu metod, które agregacji umożliwiają przesłonięcie podtypów projektów w projektach podstawowych.  
  
|Metody zastąpione przez agregację|Podtyp projektu|  
|---------------------------------------|---------------------|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Włącza podtyp projektu do<br /><br /> -Zmień podpis i ikonę węzła projektu.<br />— Całkowicie Przesłoń `Browse` obiekt projektu.<br />— Określ, czy można zmienić nazwę projektu.<br />— Określ kolejność sortowania.<br />-Kontrola kontekstu użytkownika w celu zapewnienia dynamicznej pomocy.|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Włącza podtyp projektu do kontrolowania, jakie usługi kontekstowe są udostępniane projektantom i edytorom.|  
|Z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Włącza podtyp projektu do<br /><br /> — Uczestnictwo w kierowaniu poleceń dla poleceń projektu.<br />-Dodawanie, usuwanie lub wyłączanie obu poleceń otoczenia projektu i Eksplorator rozwiązań aktywnych poleceń.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Włącza podtype projektu do filtrowania zawartości widocznej dla użytkownika w oknie dialogowym **Dodaj nowy element** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Włącza podtyp projektu do<br /><br /> -Określ domyślny Generator przyznany przez rozszerzenie pliku.<br />-Mapuje nazwę generatora czytelnego przez człowieka na obiekt COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Właściwości używane przez podtypy projektu  
 Środowisko i system projektu podstawowego mogą używać właściwości z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> wyliczenia szczegółowo opisanych w poniższej tabeli, aby umożliwić podtype projektu sterowanie różnymi funkcjami systemu projektu.  
  
|Właściwość VSHPROPID|Podtyp projektu|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Umożliwia podtype projektu kontrolowanie zawartości okna dialogowego **Dodawanie elementu** . Podtyp projektu może zapewnić nową specyfikację katalogów szablonów, dodać nowe rodzaje elementów, usunąć istniejące elementy i ponownie zorganizować podzestaw elementów w oknie dialogowym **Dodaj element** projektu podstawowego.|  
|`PropertyPagesCLSIDList`|Umożliwia podtype projektu Dodawanie lub usuwanie stron właściwości niezależnych od konfiguracji.|  
|`CfgPropertyPagesCLSIDList`|Umożliwia podtype projektu Dodawanie lub usuwanie stron właściwości zależnych od konfiguracji.|  
|`ExtObjectCATID`|Umożliwia podtype projektu, aby zapewnić rozszerzenie automatyzacji dla obiektów projektu lub elementu projektu, wiedząc, że rozszerza CATID. Na przykład podtyp projektu może dostarczyć `Project.Extender("<subtype>")` obiekt niestandardowy.|  
|`BrowseObjectCATID`|Umożliwia podtype projektu, aby zapewnić rozszerzenie automatyzacji dla `Browse` obiektu, wiedząc, że rozszerza CATID. Na przykład podtyp projektu może dodać do kolekcji dodatkowe właściwości <xref:EnvDTE.Project.Properties%2A> .|  
|`CfgBrowseObjectCATID`|Umożliwia podtype projektu, aby zapewnić rozszerzenie automatyzacji dla obiektu przeglądania konfiguracji projektu. Na przykład podtyp projektu może dodać do kolekcji dodatkowe właściwości <xref:EnvDTE.Configuration.Properties%2A> .|  
|`CfgExtObjectCATID`|Umożliwia podtype projektu, aby zapewnić rozszerzenie automatyzacji dla obiektu konfiguracji.|  
|`DefaultPlatformName`|Umożliwia podtype projektu określenie nazwy platformy dla obiektów konfiguracji projektu.|  
  
 Projekt podstawowy zawiera domyślną implementację powyższych właściwości. Projekt podstawowy pobiera te metody, wywołując `QueryInterface` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> zewnętrznego podtypu projektu, co umożliwia przesłonięcie implementacji właściwości przez podtyp projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)
