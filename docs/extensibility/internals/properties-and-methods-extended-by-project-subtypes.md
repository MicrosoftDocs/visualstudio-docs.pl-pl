---
title: Właściwości i metody rozszerzone o podtypy projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706197"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Właściwości i metody rozszerzane przez podtypy projektów
Podtyp projektu ma dużą moc, aby wpłynąć na zachowanie projektu, ponieważ jest skonstruowany jako agregator projektu podstawowego. W tej sekcji podsumowano niektóre funkcje, które można ulepszyć lub zmodyfikować według podtypów projektu.

## <a name="features-gained-by-aggregation"></a>Funkcje uzyskane przez agregację
 W poniższej tabeli podsumowano wiele metod, które agregacja umożliwia podtypy projektu zastąpić w projektach podstawowych.

|Metody zastąpione przez agregację|Podtyp projektu|
|---------------------------------------|---------------------|
|Od: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Umożliwia podtyp projektu<br /><br /> - Zmień podpis i ikonę węzła projektu.<br />- Całkowicie zastąpić `Browse` obiekt projektu.<br />- Kontroluj, czy można zmienić nazwę projektu.<br />- Sterowanie kolejnością sortowania.<br />- Kontroluj kontekst użytkownika dla dynamicznej pomocy.|
|Od: <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umożliwia podtyp projektu, aby kontrolować, jakie usługi kontekstowe są dostarczane projektantom i redaktorom.|
|Od: <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Umożliwia podtyp projektu<br /><br /> - Weź udział w routingu poleceń dla poleceń projektu.<br />- Dodaj, usuń lub wyłącz oba polecenia otoczenia projektu i polecenia aktywne w Eksploratorze rozwiązań.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Umożliwia podtyp projektu filtrować to, co użytkownik widzi w oknie dialogowym **Dodawanie nowego elementu.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Umożliwia podtyp projektu<br /><br /> - Określ domyślny generator danego rozszerzenia pliku.<br />- Mapowanie nazwy generatora czytelnego dla człowieka na obiekt COM.|

## <a name="properties-used-by-project-subtypes"></a>Właściwości używane przez podtypy projektu
 Środowisko i podstawowy system projektu można <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> użyć <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> właściwości i wyliczenia wyszczególnione w poniższej tabeli, aby włączyć podtyp projektu do kontrolowania różnych funkcji systemu projektu.

|VSHPROPID, właściwość|Podtyp projektu|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Umożliwia podtyp projektu do kontrolowania zawartości okna dialogowego **Dodawanie elementu.** Podtyp projektu może dostarczyć nową specyfikację katalogów szablonów, dodać nowe rodzaje elementów, usunąć istniejące elementy i zreorganizować podzbiór elementów w oknie dialogowym **Dodawanie elementu** projektu podstawowego.|
|`PropertyPagesCLSIDList`|Umożliwia podtyp projektu, aby dodać lub usunąć strony właściwości niezależne od konfiguracji.|
|`CfgPropertyPagesCLSIDList`|Umożliwia podtyp projektu, aby dodać lub usunąć strony właściwości zależne od konfiguracji.|
|`ExtObjectCATID`|Umożliwia podtyp projektu, aby zapewnić rozszerzenie automatyzacji dla projektu lub obiektów elementu projektu, znając Extender CATID. Na przykład podtyp projektu może `Project.Extender("<subtype>")` dostarczyć obiekt niestandardowy.|
|`BrowseObjectCATID`|Umożliwia podtyp projektu, aby zapewnić `Browse` rozszerzenie automatyzacji dla obiektu, znając Extender CATID. Na przykład podtyp projektu można dodać <xref:EnvDTE.Project.Properties%2A> dodatkowe właściwości do kolekcji.|
|`CfgBrowseObjectCATID`|Umożliwia podtyp projektu, aby zapewnić rozszerzenie automatyzacji dla obiektu przeglądania konfiguracji projektu. Na przykład podtyp projektu można dodać <xref:EnvDTE.Configuration.Properties%2A> dodatkowe właściwości do kolekcji.|
|`CfgExtObjectCATID`|Umożliwia podtyp projektu, aby zapewnić rozszerzenie automatyzacji dla obiektu konfiguracji.|
|`DefaultPlatformName`|Umożliwia podtyp projektu, aby określić nazwę platformy dla obiektów konfiguracji projektu.|

 Projekt podstawowy zapewnia domyślną implementację powyższych właściwości. Projekt podstawowy pobiera je, wywołując `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> na najbardziej zewnętrzny podtyp projektu, umożliwiając w ten sposób podtyp projektu zastąpić implementację właściwości.

## <a name="see-also"></a>Zobacz też
- [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)
