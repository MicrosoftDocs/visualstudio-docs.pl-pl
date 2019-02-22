---
title: Podstawowe składniki modelu projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e7139b92467c0b6622accce9530abf3e75fcea0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636154"
---
# <a name="project-model-core-components"></a>Podstawowe składniki modelu projektu
Rozwiń następujące tabele w modelu projektu. Tabele zawierają krótkie opisy interfejsów i usług określonych w modelu, interfejsy i usługi związane z określonymi obiektami. Ponadto tabele szczegółowo opisano inne interfejsy, które są opcjonalne w tworzenie projektu i konserwację, w zależności od wymagań danego typu określonego projektu.

 Aby uzyskać więcej informacji, zobacz [narzędzi do przeglądania symboli obsługi](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Obiekt pakietu

|Interface|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicjuje VSPackage w środowisku IDE i udostępnia jej usługi do środowiska IDE programu.|

### <a name="project-factory-object"></a>Obiekt fabryki projektu

|Interface|Komentarze|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Zarządza tworzenie nowych projektów i otworzenie istniejącego projektu.|

### <a name="project-objects"></a>Obiekty projektu

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Zarządza Dodawanie i usuwanie elementów projektu, otwiera edytory i utrzymuje mapowanie między moniker każdego dokumentu i `VSITEMID`. Dziedziczy `IVsProject` i `IVsProject2`.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Zarządza właściwości nawigacji i wyświetlania i dostępne są zdarzenia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Wykonywanie, podobnie jak w przypadku polecenia umożliwia `IOleCommandTarget` dla poleceń, takich jak wycinanie i zmiany nazwy, które są stosowane tylko wtedy, gdy fokus jest w Eksploratorze rozwiązań.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Służy jako interfejs docelowy polecenia głównej w hierarchii projektu. Jest to standardowy interfejs do tworzenia zapytań o obiekty do ich stanu lub stanu i uruchamianie poleceń. Dostępne, gdy nie koncentrują się w oknie projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Służy do koordynowania trwałości stanu projektu. Zazwyczaj stanu projektu jest przechowywany jako plik projektu, ale mogą być dostosowane do systemów pamięci masowej, które nie są oparte na plikach.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umożliwia projekt, aby zarządzać wszystkimi aspektami stanów trwałych dla elementów projektu, albo jako pliki na dysku lub obiektów w innych systemach magazynowania. `IVsPersistHierarchyItem2` Interfejs jest używany dla elementów, które nie implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Służy do koordynowania interakcji z kontrolą kodu źródłowego.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umożliwia projekty do zarządzania informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Zarządza obiektów konfiguracji projektu, takich jak konfiguracja debugowania/oficjalnych. Tworzenie, wdrażanie i debugowanie operacje są koordynowane za pośrednictwem obiektów konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementowany przez hierarchie kontrolować delete (destrukcyjne) lub Usuń (nieszkodliwe) opcji hierarchię elementów. Wywołaj interfejs zapytań dla `IVsHierarchyDeleteHandler` interfejs z `IVsHierarchy` interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Udostępnia opcję wdrażania obiekt, który obsługuje `IVsCfgProvider2` interfejsu na inną tożsamość COM niż obiekt projektu, który implementuje `IVsHierarchy` interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Opcjonalny interfejs zaimplementowane się projekt extensible przez innych programistów. `IVsProjectStartupServices` Interfejs umożliwia VSPackage innej firmy można zarejestrować identyfikator GUID, który utrwalanie w pliku projektu, tak, aby za każdym razem, gdy projekt ładuje, ładowania usługi innych firm identyfikator GUID w pliku projektu sieci Web i wywołanie `QueryService` dla tego identyfikatora GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementowany przez hierarchii źródłowej w `UIHierarchy` okna, aby koordynować operacje schowka, takich jak wycinania, kopiowania i wklejania. Użyj `AdviseClipboardHelperEvents` interfejsu do rejestrowania zdarzeń do Schowka.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Informacje na temat przeciąganego elementu względem jego źródło danych podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływane z `IVsHierarchy` interfejsu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Informacje na temat przeciąganego elementu względem jego miejsca docelowego podczas operacji przeciągania i upuszczania w oknie hierarchii interfejsu użytkownika. Wywoływane z `IVsHierarchy` interfejsu.|

### <a name="configuration-object"></a>Obiekt konfiguracji

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Zawiera informacje o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umożliwia projekty do zarządzania informacjami o konfiguracji.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Umożliwia projektu do uruchamiania pod kontrolą debugera.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementowany przez projekty wdrażania, wykonujące operacje wdrażania w innych projektach.|

### <a name="configuration-builder-object"></a>Obiekt konstruktora konfiguracji

|Interfejsy|Komentarze|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Zarządza operacji tworzenia konfiguracji projektu.|

### <a name="additional-project-objects"></a>Dodatkowe obiekty projektu

|Interfejsy|Komentarze|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Wyświetla elementu właściwości w **właściwości** okna.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Wyświetla dane wyjściowe dla wdrożenia.|

 W poniższej tabeli przedstawiono krótkie opisy usług określonych w modelu projektu.

### <a name="services"></a>Usługi

|Usługa|Komentarze|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Używać pakietów VSPackage, który implementuje typy projektów, aby zarejestrować, ich fabryka projektu istnieje w środowisku IDE. Usługi pakietu VSPackage musi wywołać `QueryService` dla tej usługi, a następnie zarejestrować jego fabryki projektu podczas `IVsPackage::SetSite` metoda jest wywoływana. Jeśli `SetSite` metoda nie jest wywoływana, projekt nie zostanie uruchomiony.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Zapewnia dostęp do środowiska IDE wewnętrznego, wbudowane pojęcie bieżącego rozwiązania, takimi jak wyliczyć projektów, tworzyć nowe projekty, zwróć uwagę na zmiany projektu i tak dalej.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Metoda wywoływana przez projekty, które chcą uczestniczyć w kontroli źródła.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Przechowuje spis otwarte dokumenty, aby ustalić, czy co najmniej jeden z elementów projektu jest już otwarty.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Zawiera interfejsy i metody o nazwie faktycznie otworzyć element projektu za pomocą edytora standardowego lub określonego edytora.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Wymagane, wywoływana przez wszystkie projekty, gdy ich dodać, usunąć lub zmienić ich elementów.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Zarządza zmiany pliku lub katalogu, a następnie powiadamia klientów, gdy wybrane pliki zostały zmienione na dysku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Wymagane do wywołania przez wszystkich projektach i edytorach przed ich zakłóconych elementów lub je zapisać.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Zarządza kolejność operacji kompilowania i wdrażania dla konfiguracji projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Zapewnia dostęp do niskiego poziomu debugera, obejmujący usługi używane dla większości kontrolek debugowania.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Pozwala pakietów VSPackage dostęp do informacji o bieżący wybór oraz umożliwia komunikację z **właściwości** okna.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Zapewnia podstawowe funkcje IDE związane z interfejsem użytkownika, takie jak możliwość tworzenia i wyliczenia okna narzędzi lub okna dokumentu lub zgłosić błąd użytkownikowi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Zapewnia dostęp do pasku stanu środowiska IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Używany do implementowania modelu automatyzacji. W modelu projektu, nastąpi powrót obiektu właściwości, która umożliwia tworzy wystąpienie tego obiektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Umożliwia Implementowanie zdarzenia Schowka na obiekt projektu w hierarchii. `SVsUIHierWinClipboardHelper` Umożliwia prawidłowo uchwytu wycinanie, kopiowanie i wklejanie.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Nie w kompilacji: Używanie klas projektu HierUtil7 do zaimplementowania typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)