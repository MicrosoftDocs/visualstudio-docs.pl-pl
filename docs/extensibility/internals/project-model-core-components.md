---
title: Podstawowe składniki modelu projektu | Microsoft Docs
description: Ten artykuł zawiera opisy interfejsów i usług zidentyfikowanych w rdzeniu modelu projektu oraz interfejsów i usług skojarzonych z obiektami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88dc53378e7e06d0a7d4ad362f7bb3876e186c80
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899709"
---
# <a name="project-model-core-components"></a>Podstawowe składniki modelu projektu
Poniższe tabele rozszerzają model projektu. Tabele zawierają krótkie opisy interfejsów i usług zidentyfikowanych w modelu oraz interfejsów i usług skojarzonych z określonymi obiektami. Ponadto tabele zawierają szczegóły innych interfejsów, które są opcjonalne podczas tworzenia i konserwacji projektu, w zależności od wymagań określonego typu projektu.

 Aby uzyskać więcej informacji, [zobacz Supporting Symbol-Browsing Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md)(Narzędzia Symbol-Browsing narzędzi).

### <a name="package-object"></a>Obiekt pakietu

|Interfejs|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicjuje pakiet VSPackage w idee IDE i udostępnia jego usługi w tym idee.|

### <a name="project-factory-object"></a>Project Factory, obiekt

|Interfejs|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Zarządza tworzeniem nowych projektów i otwieraniem istniejących projektów.|

### <a name="project-objects"></a>Obiekty projektu

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Zarządza dodawaniem i usuwaniem elementów projektu, otwiera edytory i obsługuje mapowanie między poszczególnymi monikerami dokumentów i `VSITEMID` . Dziedziczy z `IVsProject` i `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Zarządza nawigacją i właściwościami wyświetlania oraz udostępnia zdarzenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Umożliwia wykonywanie poleceń podobnych do polecenia dla poleceń, takich jak Wytnij i Zmień nazwę, które mają zastosowanie tylko wtedy, gdy `IOleCommandTarget` fokus Eksplorator rozwiązań.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Służy jako podstawowy interfejs docelowy polecenia dla hierarchii projektu. Jest to standardowy interfejs do wykonywania zapytań o obiekty w celu ich stanu polecenia lub stanu i uruchamiania poleceń. Dostępne, gdy nie skupiasz się na oknie Projekt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordynuje trwałość stanu projektu. Zazwyczaj stan projektu jest przechowywany jako plik projektu, ale można go dostosować do systemów magazynowania, które nie są oparte na plikach.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umożliwia projektowi zarządzanie wszystkimi aspektami trwałości elementów projektu, zarówno jako plikami na dysku, jak i obiektami w innych systemach magazynowania. Interfejs `IVsPersistHierarchyItem2` jest używany dla elementów, które nie implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordynuje interakcje z kontrolą kodu źródłowego.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umożliwia projektom zarządzanie informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Zarządza obiektami konfiguracji projektu, takimi jak konfiguracje debugowania/wydania. Operacje kompilacji, wdrażania i debugowania są koordynowane za pośrednictwem obiektów konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Zaimplementowane przez hierarchie w celu kontrolowania opcji usuwania (destrukcyjnego) lub usuwania (niedestrukcyjnego) elementów hierarchii. Wywołaj interfejs zapytania w `IVsHierarchyDeleteHandler` interfejsie z `IVsHierarchy` interfejsu .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Udostępnia opcję implementacji obiektu, który obsługuje interfejs w innej tożsamości COM niż obiekt projektu, `IVsCfgProvider2` który implementuje `IVsHierarchy` interfejs.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Zaimplementowano opcjonalny interfejs, aby projekt był rozszerzalny przez innych deweloperów. Interfejs umożliwia pakietowi VSPackage innej firmy zarejestrowanie identyfikatora GUID utrwalonego w pliku projektu, dzięki czemu przy każdym załadowaniu projektu należy załadować identyfikator GUID usługi innej firmy do pliku projektu i wywołać ten identyfikator `IVsProjectStartupServices` `QueryService` GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Zaimplementowane przez hierarchie źródłowe w `UIHierarchy` oknie w celu koordynowania operacji schowka, takich jak wycinanie, kopiowanie i wklejanie. Użyj `AdviseClipboardHelperEvents` interfejsu do rejestrowania zdarzeń schowka.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Zawiera informacje o przeciąganym elementie względem jego źródła danych podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływana z `IVsHierarchy` interfejsu .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Zawiera informacje o przeciąganym elementie względem jego celu upuszczania podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływana z `IVsHierarchy` interfejsu .|

### <a name="configuration-object"></a>Obiekt konfiguracji

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Zawiera informacje o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umożliwia projektom zarządzanie informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Umożliwia uruchamianie projektu pod kontrolą debugera.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Zaimplementowane przez projekty wdrażania, które wykonują operacje wdrażania dla innych projektów.|

### <a name="configuration-builder-object"></a>Obiekt programu Configuration Builder

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Zarządza operacją kompilacji konfiguracji projektu.|

### <a name="additional-project-objects"></a>Dodatkowe obiekty project

|Interfejsy|Komentarze|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Wyświetla właściwości elementu w **oknie** Właściwości.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Wyświetla dane wyjściowe dotyczące wdrożenia.|

 W poniższej tabeli przedstawiono krótkie opisy usług zidentyfikowanych w modelu projektu.

### <a name="services"></a>Usługi

|Usługa|Komentarze|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Używane przez pakiet VSPackages, które implementują typy projektów w celu zarejestrowania, że ich fabryka projektów istnieje w ide. Pakiet VSPackage musi wywołać `QueryService` tę usługę i zarejestrować fabrykę projektu po `IVsPackage::SetSite` wywołaniu metody. Jeśli metoda `SetSite` nie zostanie wywołana, nie zostanie utworzyć wystąpienia projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia dostęp do wewnętrznego, wbudowanego w ideę bieżącego rozwiązania, takiego jak możliwość wyliczania projektów, tworzenia nowych projektów, zauważenia zmian projektu i tak dalej.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Wywoływane przez projekty, które chcą uczestniczyć w kontroli źródła.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Utrzymuje tabelę otwartych dokumentów, aby określić, czy co najmniej jeden element projektu jest już otwarty.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Zawiera interfejsy i metody wywoływane w celu otwarcia elementu projektu przy użyciu standardowego edytora lub określonego edytora.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Wymagane do wywoływania przez wszystkie projekty podczas dodawania, usuwania lub zmieniania nazw elementów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Zarządza zmianami w pliku lub katalogu i powiadamia klientów o zmianie wybranych plików na dysku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Wymagane, aby były wywoływane przez wszystkie projekty i edytory, zanim zanieczyszczone elementy lub je zapiszą.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Zarządza kolejnością operacji kompilacji i wdrażania dla konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Zapewnia dostęp do usług debugera niskiego poziomu używanych w większości kontrolek debugowania.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Umożliwia pakietom VSPackage dostęp do informacji o bieżących wyborach i umożliwia komunikację z **oknem** Właściwości.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Zapewnia podstawowe funkcje środowiska IDE związane z interfejsem użytkownika, takie jak możliwość tworzenia i wyliczania okien narzędzi lub okien dokumentów albo zgłaszania błędu użytkownikowi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Zapewnia dostęp do paska stanu środowiska IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Służy do implementowanie modelu automatyzacji. W modelu projektu zostanie zwrócony obiekt właściwości, który umożliwia utworzenie wystąpienia tego obiektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Służy do implementowania zdarzeń schowka w obiekcie projektu w hierarchii. `SVsUIHierWinClipboardHelper` Polecenie umożliwia poprawne obsługę operacji wycinania, kopiowania i wklejania.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Nie w kompilacji: implementowanie typu projektu przy użyciu klas projektu HierUtil7 (C++)](/previous-versions/bb166212(v=vs.100))
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)