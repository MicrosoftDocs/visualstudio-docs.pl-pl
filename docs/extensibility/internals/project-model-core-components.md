---
title: Podstawowe składniki modelu projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706538"
---
# <a name="project-model-core-components"></a>Podstawowe składniki modelu projektu
Poniższe tabele rozwiń w modelu projektu. Tabele przedstawiają krótkie opisy interfejsów i usług określonych w modelu oraz interfejsów i usług skojarzonych z określonymi obiektami. Ponadto tabele szczegółowo inne interfejsy, które są opcjonalne w tworzeniu projektu i konserwacji w zależności od wymagań określonego typu projektu.

 Aby uzyskać więcej informacji, zobacz [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Obiekt pakietu

|Interface|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicjuje VSPackage w IDE i udostępnia swoje usługi ide.|

### <a name="project-factory-object"></a>Obiekt Fabryka projektu

|Interface|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Zarządza tworzeniem nowych projektów i otwieraniem istniejących projektów.|

### <a name="project-objects"></a>Obiekty projektu

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Zarządza dodawaniem i usuwaniem elementów projektu, otwiera edytory i utrzymuje `VSITEMID`mapowanie między każdym monikerem dokumentu a programem . Dziedziczy `IVsProject` po `IVsProject2`i .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Zarządza właściwościami nawigacji i wyświetlania oraz udostępnia zdarzenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Włącza wykonywanie poleceń `IOleCommandTarget` podobne do polecenia dla poleceń, takich jak Wytnij i Zmień nazwę, które mają zastosowanie tylko wtedy, gdy fokus znajduje się w Eksploratorze rozwiązań.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Służy jako interfejs docelowy polecenia podstawowego dla hierarchii projektu. Jest to standardowy interfejs do wykonywania zapytań o ich stan polecenia lub stan i uruchomione polecenia. Dostępne, gdy nie koncentrujesz się w oknie Projekt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordynuje trwałość stanu projektu. Zazwyczaj stan projektu jest przechowywany jako plik projektu, ale można go dostosować do systemów magazynowania, które nie są oparte na plikach.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umożliwia projektowi zarządzanie wszystkimi aspektami trwałości dla jego elementów projektu, jako pliki na dysku lub obiekty w innych systemach magazynu. Interfejs `IVsPersistHierarchyItem2` jest używany dla elementów, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> które nie implementują interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordynuje interakcje z kontrolą kodu źródłowego.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umożliwia projektom zarządzanie informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Zarządza obiektami konfiguracji projektu, takimi jak konfiguracje debugowania/zwalniania. Operacje kompilacji, wdrażania i debugowania są koordynowane za pomocą obiektów konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementowane przez hierarchie do kontrolowania opcji usuwania (destrukcyjne) lub usunąć (nieniszczące) dla elementów hierarchii. Wywołaj interfejs `IVsHierarchyDeleteHandler` zapytania w `IVsHierarchy` interfejsie z interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Udostępnia opcję implementacji posiadania obiektu, `IVsCfgProvider2` który obsługuje interfejs na innej tożsamości COM `IVsHierarchy` niż obiekt projektu, który implementuje interfejs.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Opcjonalny interfejs zaimplementowany w celu rozszerzenia projektu przez innych deweloperów. Interfejs `IVsProjectStartupServices` umożliwia vspackage innej firmy do zarejestrowania identyfikatora GUID, który można upierać się w pliku projektu, tak aby za `QueryService` każdym razem, gdy projekt ładuje, załadować identyfikator GUID usługi innej firmy do pliku projektu i wywołać ten identyfikator GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementowane przez hierarchie `UIHierarchy` źródłowe w oknie w celu koordynowania operacji schowka, takich jak wycinanie, kopiowanie i wklejenie. Użyj `AdviseClipboardHelperEvents` interfejsu, aby zarejestrować zdarzenia schowka.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Zawiera informacje o przeciągniętym elemencie względem jego źródła danych podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływana `IVsHierarchy` z interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Zawiera informacje o przeciągniętym elemencie względem jego celu upuszczania podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływana `IVsHierarchy` z interfejsu.|

### <a name="configuration-object"></a>Obiekt konfiguracji

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Zawiera informacje o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umożliwia projektom zarządzanie informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Umożliwia uruchomienie projektu pod kontrolą debugera.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementowane przez projekty wdrażania, które wykonują operacje wdrażania dla innych projektów.|

### <a name="configuration-builder-object"></a>Obiekt Konstruktor konfiguracji

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Zarządza operacją kompilacji konfiguracji projektu.|

### <a name="additional-project-objects"></a>Dodatkowe obiekty projektu

|Interfejsy|Komentarze|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Wyświetla właściwości elementu w oknie **Właściwości.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Wyświetla dane wyjściowe dla wdrożenia.|

 W poniższej tabeli przedstawiono krótkie opisy usług określonych w modelu projektu.

### <a name="services"></a>Usługi

|Usługa|Komentarze|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Używane przez VSPackages, które implementują typy projektów, aby zarejestrować, że ich fabryka projektu istnieje z IDE. VsPackage musi `QueryService` wywołać tę usługę i `IVsPackage::SetSite` zarejestrować jego fabryki projektu, gdy metoda jest wywoływana. Jeśli `SetSite` metoda nie jest wywoływana, projekt nie jest tworzone.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia dostęp do ide wewnętrzne, wbudowane pojęcie bieżącego rozwiązania, takie jak możliwość wyliczanie projektów, tworzenie nowych projektów, zwracać uwagę na zmiany projektu i tak dalej.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Wywoływane przez projekty, które chcą uczestniczyć w kontroli źródła.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Przechowuje tabelę otwartych dokumentów, aby ustalić, czy jeden lub więcej elementów projektu jest już otwartych.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Zawiera interfejsy i metody wywoływane w celu rzeczywistego otwarcia elementu projektu przy użyciu standardowego edytora lub określonego edytora.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Wymagane jest wywoływanie przez wszystkie projekty podczas dodawania, usuwania lub zmieniania nazwy elementów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Zarządza zmianami w pliku lub katalogu i powiadamia klientów o zmianie wybranych plików na dysku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Wymagane, aby być wywoływane przez wszystkie projekty i redaktorów, zanim brudne elementy lub zapisać je.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Zarządza kolejnością operacji kompilacji i wdrażania dla konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Zapewnia dostęp do usług debugera niskiego poziomu używanych do większości formantów debugowania.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Umożliwia vspackages dostęp do informacji o bieżących wyborów i umożliwia komunikację z **właściwości** okna.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Zapewnia podstawowe funkcje IDE związane z interfejsem użytkownika, takie jak możliwość tworzenia i wyliczania okien narzędzi lub okien dokumentów lub zgłaszania błędu użytkownikowi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Zapewnia dostęp do paska stanu IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Służy do implementowania modelu automatyzacji. W modelu projektu zwrócisz obiekt właściwości, który umożliwia utworzenie wystąpienia tego obiektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Służy do implementowania zdarzeń schowka na obiekcie projektu w hierarchii. `SVsUIHierWinClipboardHelper`umożliwia prawidłowe obsługę operacji wycinania, kopiowania i wklejania.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Nie w kompilacji: za pomocą HierUtil7 klasy projektu do zaimplementowania typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
