---
title: Właściwości i metody rozszerzone przez podtypy projektów | Microsoft Docs
description: Dowiedz się więcej o funkcjach, które można ulepszać lub modyfikować podtypy projektów, co pozwala dostosować zachowanie systemów projektu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ddcf020cf0b3e3e4f0f4a7c61ff1f15ce9ded5e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903544"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Właściwości i metody rozszerzane przez podtypy projektów
Podtyp projektu ma dużą moc, aby wpłynąć na zachowanie projektu, ponieważ jest konstruowany jako agregator projektu podstawowego. Ta sekcja zawiera podsumowanie niektórych funkcji, które można ulepszyć lub zmodyfikować za pomocą podtypów projektów.

## <a name="features-gained-by-aggregation"></a>Funkcje uzyskane przez agregację
 W poniższej tabeli podsumowano wiele metod, które agregacja umożliwia zastępowanie podtypów projektów w projektach podstawowych.

|Metody zastąpione przez agregację|Podtyp projektu|
|---------------------------------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Z:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Włącza podtyp projektu na<br /><br /> — Zmień podpis i ikonę węzła projektu.<br />— Całkowicie zastąp obiekt `Browse` projektu.<br />— Kontroluj, czy można zmienić nazwę projektu.<br />- Kontroluj kolejność sortowania.<br />— Kontrolowanie kontekstu użytkownika w celu korzystania z pomocy dynamicznej.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>Z:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umożliwia podtyp projektu w celu kontrolowania, jakie usługi kontekstowe są udostępniane projektantom i edytorom.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Z:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Włącza podtyp projektu na<br /><br /> - Uczestniczyć w routingu poleceń dla poleceń projektu.<br />- Dodaj, usuń lub wyłącz oba polecenia otoczenia projektu i Eksplorator rozwiązań aktywnych poleceń.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Umożliwia podtypowi projektu filtrowanie tego, co użytkownik widzi w **oknie dialogowym Dodawanie nowego** elementu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Włącza podtyp projektu na<br /><br /> - Określ generator domyślny na podstawie rozszerzenia pliku.<br />- Mapowanie nazwy generatora czytelnej dla człowieka na obiekt COM.|

## <a name="properties-used-by-project-subtypes"></a>Właściwości używane przez podtypy projektów
 Środowisko i system projektu podstawowego mogą używać właściwości z wyliczeń i szczegółowo wymienionych w poniższej tabeli, aby umożliwić podtyp projektu w celu kontrolowania <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> różnych funkcji systemu projektu.

|VSHPROPID, właściwość|Podtyp projektu|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Umożliwia podtypowi projektu kontrolowanie zawartości okna **dialogowego Dodawanie** elementu. Podtyp projektu może dostarczyć nową specyfikację katalogów szablonów, dodać nowe rodzaje elementów, usunąć istniejące elementy i zreorganizować podzbiór elementów w oknie dialogowym Dodawanie elementu projektu **podstawowego.**|
|`PropertyPagesCLSIDList`|Umożliwia podtypowi projektu dodawanie lub usuwanie stron właściwości niezależnych od konfiguracji.|
|`CfgPropertyPagesCLSIDList`|Umożliwia podtypowi projektu dodawanie lub usuwanie stron właściwości zależnych od konfiguracji.|
|`ExtObjectCATID`|Umożliwia podtyp projektu w celu zapewnienia rozszerzenia automatyzacji dla obiektów projektu lub elementu projektu, znając rozszerzenie CATID. Na przykład podtyp projektu może zapewnić obiekt `Project.Extender("<subtype>")` niestandardowy.|
|`BrowseObjectCATID`|Umożliwia podtyp projektu, aby zapewnić rozszerzenie automatyzacji dla `Browse` obiektu, znając identyfikator CATID rozszerzenia. Na przykład podtyp projektu może dodać dodatkowe właściwości do <xref:EnvDTE.Project.Properties%2A> kolekcji.|
|`CfgBrowseObjectCATID`|Umożliwia podtypowi projektu zapewnienie rozszerzenia automatyzacji dla obiektu przeglądania konfiguracji projektu. Na przykład podtyp projektu może dodać dodatkowe właściwości do <xref:EnvDTE.Configuration.Properties%2A> kolekcji.|
|`CfgExtObjectCATID`|Umożliwia podtypowi projektu zapewnienie rozszerzenia automatyzacji dla obiektu konfiguracji.|
|`DefaultPlatformName`|Umożliwia określenie nazwy platformy dla obiektów konfiguracji projektu podtypu projektu.|

 Projekt podstawowy udostępnia domyślną implementację powyższych właściwości. Projekt podstawowy pobiera je, wywołując metodę dla najbardziej zewnętrznego podtypu projektu, dzięki czemu podtyp projektu może przesłonić `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> implementację właściwości.

## <a name="see-also"></a>Zobacz też
- [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)
