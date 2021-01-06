---
title: Podstawowe składniki modelu projektu | Microsoft Docs
description: Ten artykuł zawiera opisy interfejsów i usług zidentyfikowanych w podstawowym modelu projektu oraz interfejsy i usługi skojarzone z obiektami.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c6aeb24b2aee5b0abb3e5d803004ba97725bb707
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876899"
---
# <a name="project-model-core-components"></a>Podstawowe składniki modelu projektu
Poniższe tabele rozszerzają model projektu. Tabele przedstawiają krótkie opisy interfejsów i usług identyfikowanych w modelu oraz interfejsy i usługi skojarzone z określonymi obiektami. Ponadto w tabelach szczegółowo opisano inne interfejsy, które są opcjonalne podczas tworzenia i konserwacji projektu, w zależności od wymagań określonego typu projektu.

 Aby uzyskać więcej informacji, zobacz temat [obsługa Symbol-Browsing narzędzia](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Obiekt pakietu

|Interfejs|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicjuje pakietu VSPackage w środowisku IDE i udostępnia swoje usługi dla środowiska IDE.|

### <a name="project-factory-object"></a>Obiekt fabryki projektu

|Interfejs|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Zarządza tworzeniem nowych projektów i otwiera istniejące projekty.|

### <a name="project-objects"></a>Obiekty projektu

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Zarządza dodawaniem i usuwaniem elementów projektu, otwiera edytory i utrzymuje mapowanie między każdym monikerem dokumentu a `VSITEMID` . Dziedziczy z `IVsProject` i `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Zarządza nawigacją i właściwościami wyświetlania oraz wyświetla zdarzenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Włącza wykonywanie poleceń podobnie `IOleCommandTarget` jak w przypadku poleceń, takich jak wycinanie i zmiana nazwy, które są stosowane tylko wtedy, gdy fokus jest w Eksplorator rozwiązań.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Służy jako interfejs docelowy polecenia podstawowego dla hierarchii projektu. Jest to standardowy interfejs do wykonywania zapytań dotyczących obiektów w przypadku ich stanu lub stanu polecenia oraz uruchamiania poleceń. Dostępne, gdy nie masz fokusu w oknie projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordynuje trwałość stanu projektu. Zazwyczaj stan projektu jest przechowywany jako plik projektu, ale można go dostosować do systemów magazynowania, które nie są oparte na plikach.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umożliwia projektowi zarządzanie wszystkimi aspektami trwałości dla elementów projektu, takich jak pliki na dysku lub obiekty w innych systemach magazynowania. `IVsPersistHierarchyItem2`Interfejs jest używany dla elementów, które nie implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordynuje interakcje z kontrolą kodu źródłowego.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umożliwia projektom zarządzanie informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Zarządza obiektami konfiguracji projektu, takimi jak konfiguracje debugowania/wydawania. Operacje kompilowania, wdrażania i debugowania są koordynowane za poorednictwem obiektów konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Zaimplementowane przez hierarchie w celu kontrolowania opcji usuwania (niszczących) lub usuwania (nieniszczących) dla elementów hierarchii. Wywoływanie interfejsu zapytania w `IVsHierarchyDeleteHandler` interfejsie z `IVsHierarchy` interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Zapewnia opcję implementacji obiektu, który obsługuje `IVsCfgProvider2` interfejs na innej tożsamości com niż obiekt projektu, który implementuje `IVsHierarchy` interfejs.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Opcjonalny interfejs zaimplementowany, aby projekt był rozszerzalny przez innych deweloperów. `IVsProjectStartupServices`Interfejs umożliwia pakietu vspackageom innych firm Rejestrowanie identyfikatora GUID, który utrzymuje się w pliku projektu, tak aby przy każdym załadowaniu projektu załadować identyfikator GUID usługi innej firmy do pliku projektu i wywołać `QueryService` dla tego identyfikatora GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Zaimplementowane przez hierarchie źródłowe w `UIHierarchy` oknie, aby koordynować Operacje schowka, takie jak wycinanie, kopiowanie i wklejanie. Użyj `AdviseClipboardHelperEvents` interfejsu, aby zarejestrować zdarzenia Schowka.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Zawiera informacje na temat przeciąganego elementu względem jego źródła danych podczas operacji przeciągania i upuszczania w oknie hierarchia interfejsu użytkownika. Wywoływana z `IVsHierarchy` interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Zawiera informacje o przeciąganym elemencie względem obiektu docelowego upuszczania podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływana z `IVsHierarchy` interfejsu.|

### <a name="configuration-object"></a>Obiekt konfiguracji

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Zawiera informacje o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umożliwia projektom zarządzanie informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Umożliwia uruchomienie projektu pod kontrolą debugera.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Zaimplementowane przez projekty wdrażania, które wykonują operacje wdrażania dla innych projektów.|

### <a name="configuration-builder-object"></a>Obiekt konstruktora konfiguracji

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Zarządza operacją kompilacji konfiguracji projektu.|

### <a name="additional-project-objects"></a>Dodatkowe obiekty projektu

|Interfejsy|Komentarze|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Wyświetla właściwości elementu w oknie **Właściwości** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Wyświetla dane wyjściowe wdrożenia.|

 W poniższej tabeli przedstawiono krótkie opisy usług zidentyfikowanych w modelu projektu.

### <a name="services"></a>Usługi

|Usługa|Komentarze|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Używane przez pakietów VSPackage, które implementują typy projektów, aby zarejestrować swoją fabrykę projektu w środowisku IDE. Pakietu VSPackage musi wywoływać `QueryService` tę usługę i zarejestrować jej fabrykę projektu, gdy `IVsPackage::SetSite` wywoływana jest metoda. Jeśli `SetSite` Metoda nie jest wywoływana, projekt nie jest skonkretyzowany.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia dostęp do wewnętrznego, wbudowanego koncepcji bieżącego rozwiązania, takiego jak możliwość wyliczania projektów, tworzenia nowych projektów, powiadamiania o zmianach projektu i tak dalej.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Wywoływane przez projekty, które chcą wziąć udział w kontroli źródła.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Utrzymuje tabelę otwartych dokumentów, aby określić, czy co najmniej jeden element projektu jest już otwarty.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Zawiera interfejsy i metody wywoływane do rzeczywistego otwierania elementu projektu przy użyciu standardowego edytora lub określonego edytora.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Wymagane do wywołania przez wszystkie projekty po ich dodaniu, usunięciu lub zmianie nazwy ich elementów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Zarządza zmianami w pliku lub katalogu i powiadamia klientów, gdy wybrane pliki zostały zmienione na dysku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Wymagane do wywołania przez wszystkie projekty i edytory, zanim zostaną one zmienione lub zapisane.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Zarządza kolejnością operacji kompilowania i wdrażania na potrzeby konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Zapewnia dostęp do usług debugera niskiego poziomu używanych w przypadku większości kontrolek debugowania.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Umożliwia pakietów VSPackage dostęp do informacji o bieżących wyborach i umożliwia komunikację z oknem **Właściwości** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Zapewnia podstawowe funkcje środowiska IDE związane z interfejsem użytkownika, takie jak możliwość tworzenia i wyliczania okien narzędzi lub okien dokumentów lub do zgłaszania błędu użytkownikowi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Zapewnia dostęp do paska stanu IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Używane do implementowania modelu automatyzacji. W modelu projektu zwrócisz obiekt właściwości, który umożliwia utworzenie wystąpienia tego obiektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Służy do implementowania zdarzeń Schowka w obiekcie projektu w hierarchii. `SVsUIHierWinClipboardHelper` umożliwia prawidłowe obsłudze operacji wycinania, kopiowania i wklejania.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Nie w kompilacji: używanie klas projektu HierUtil7 do implementowania typu projektu (C++)](/previous-versions/bb166212(v=vs.100))
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)