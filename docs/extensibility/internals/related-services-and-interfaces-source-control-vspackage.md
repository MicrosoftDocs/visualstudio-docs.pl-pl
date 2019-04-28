---
title: Powiązane usługi i interfejsy (pakiet VSPackage kontroli) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a792bc7b0c64b7e509e6d426c8b4f33c9f816276
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908564"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Powiązane usługi i interfejsy (pakiet VSPackage kontroli kodu źródłowego)
W tej sekcji przedstawiono wszystkie interfejsy dotyczące pakietu VSPackage kontroli źródła [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. Kontrola źródła pakietu VSPackage implementuje niektóre z tych interfejsów i używa innych użytkowników do wykonywania zadań kontroli źródła.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfejsy implementowane przez i pakietów VSPackage kontroli źródła
 Następujące interfejsy są opisane w [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], i do kontroli źródła pakietu VSPackage implementuje część z nich w zależności od jej zestaw żądanej funkcji. Niektóre interfejsy są oznaczone jako wymagane i muszą być zaimplementowane przez każdy formant źródła pakietu VSPackage.

 Dla tych interfejsów, które pakiet nie zawiera implementacji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnia domyślną implementację interfejsu. Należy pamiętać, że domyślna implementacja jest przeznaczony dla przypadku, gdy VSPackage nie jest zarejestrowane, a projekt nie jest kontrolowany. Kontroli źródła poprawnie w pisemnej pakietu VSPackage implementuje wszystkie niezbędne interfejsy, a nie w gestii Domyślna implementacja z tych interfejsów.

 Kontroli źródła pakietu VSPackage musi implementować prywatnej usługa, która hermetyzuje niektóre lub wszystkie z następujących interfejsów.

 Interfejsy są:

- Wymagane: Odpowiednie jednostki (projektu kontroli źródła pakietu VSPackage, wycinka kontroli źródła,) musi implementować interfejs.

- Zalecane: Jednostka powinna implementować ten interfejs; w przeciwnym razie funkcji kontroli źródła może być ograniczona.

- Opcjonalnie: jednostki można zaimplementować ten interfejs umożliwia korzystanie z bogatszego zestawu funkcji.

| Interface | Cel | Zaimplementowane przez | Implementowanie? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Edytory wywołanie tego interfejsu przed zmodyfikowaniem lub zapisanie pliku. Pakietu VSPackage kontroli źródła można wyewidencjonować pliku lub odmówić operację, jeśli wyewidencjonowanie nie powiedzie się. | Kontrola źródła pakietu VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Ten interfejs zapewnia funkcjonalność formantu podstawowego źródła dla projektów, takich jak rejestrowanie i wyrejestrowywanie projektów z kontrolą źródła i świadczenie pomocy technicznej dla podstawowego źródła kontrolki symbole. | Kontrola źródła pakietu VSPackage | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Ten interfejs jest uzyskiwana z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> przy użyciu <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funkcji, lub po prostu rzutowanie obiektu implementującego `IVsHierarchy` do `IVsSccProject2`. Służy do pobierania plików pod kontrolą źródła w projekcie lub informowania projektu bieżący stan kontroli źródła lub lokalizacji. | Projekt | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Moduł integracji używa tego interfejsu, można ustawić bieżącego aktywnego pakietu VSPackage. | Kontrola źródła pakietu VSPackage | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Ten interfejs jest oparty na modelu subskrypcji. Dowolnego pakietu VSPackage można sygnał, że chce odbierać zdarzenia dokumentów i zalecana przez powłokę w zdarzeń, które mają być. Wdrożenie i obsługiwane przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], która z kolei przekazuje zdarzenia implementowania `IVsTrackProjectDocumentsEvents2` do pakietu VSPackage. | Klasy zastępczej kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Ten interfejs umożliwia przetwarzanie wsadowe operacji odczytu/zapisu zsynchronizowane i zaawansowaną `OnQueryAddFiles` metody. | Klasy zastępczej kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Eksplorator rozwiązań** i projekty wywołać ten interfejs, gdy nowe pliki są dodawane do projektów lub zmieniono jego nazwę lub usuwane z projektów, plików i folderów. Kontrola źródła pakietu VSPackage można wyewidencjonować pliku projektu lub anulować operację. | Kontrola źródła pakietu VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Eksplorator rozwiązań** i projekty wywołać ten interfejs w odpowiedzi na wywołania metody interfejsu IVstrackProjectDocuments3. Kontrola źródła pakietu VSPackage można śledzić operacje wsadowe, synchronizację operacje odczytu/zapisu i pracy z bardziej zaawansowanych `OnQueryAddFiles` metody. | Kontrola źródła pakietu VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Ten interfejs zapewnia obsługę zarządzania rejestracji dla projektów sieci Web. | Kontrola źródła pakietu VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Ten interfejs jest używany do pobierania etykietki narzędzi dla plików pod kontrolą źródła w projektach. | Kontrola źródła pakietu VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Ten interfejs zapewnia obsługę rozszerzenie przestrzeni nazw. | Kontrola źródła pakietu VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Korzysta z pakietu VSPackage ten interfejs do integracji rozszerzenie przestrzeni nazw, do **New**, **Otwórz**, lub **Zapisz** okien dialogowych. W rezultacie projekty mogą być automatycznie dodane do kontroli źródła przy tworzeniu lub dodane do kontroli źródła, podczas zapisywania operacji jest aktywna. | Kontrola źródła pakietu VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Pakietu VSPackage używa tego interfejsu, aby zdefiniować dodatkowe glify jako symbole kontroli źródła dla węzłów w **Eksploratora rozwiązań**. | Kontrola źródła pakietu VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | **Dodaj** okno dialogowe dla projektów sieci Web używa tego interfejsu. Zapewnia metody do przeglądania dla lokalizację kontroli źródła i otwarcie projektu sieci Web, wcześniej dodany w repozytorium kontroli źródła w tej lokalizacji. | Kontrola źródła pakietu VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Ten interfejs zapewnia obsługę asynchroniczną (w tle) ładowanie projektów z kontrolą źródła. | Kontrola źródła pakietu VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Ten interfejs umożliwia projektów obserwować postęp asynchroniczne ładowanie inicjowane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>. | Projekt | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Ten interfejs umożliwia IDE kwerendy kontroli źródła active pakietu VSPackage. Wartość ustawienia kontroli źródła, które mają znaczenie, nawet wtedy, gdy nie zarejestrowane pakietu VSPackage kontroli źródła active wysyła zapytanie do środowiska IDE. Ten interfejs jest implementowany i obsługiwane przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. | Klasy zastępczej kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Ten interfejs jest używany podczas rejestrowania pakietu VSPackage kontroli źródła. | Klasy zastępczej kontroli źródła | Wymagane |
| <xref:EnvDTE.SourceControl> | Ten interfejs jest używany w usłudze automation. W efekcie udostępnia tylko funkcje, które mogą być wykonywane bez wyświetlania interfejsu użytkownika. | Kontrola źródła pakietu VSPackage | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Ten interfejs jest używany, aby zapisać ustawienia kontroli źródła w rozwiązania (.sln). Ustawienia obejmują lokalizację kontroli źródła i flagi stanu kontroli źródła. | Kontrola źródła pakietu VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Ten interfejs jest używany, aby zapisać ustawienia kontroli źródła w pliku rozwiązania, opcje (suo). Może to obejmować ustawienia kontroli źródła specyficzne dla użytkownika, takie jak lokalizacja rejestracji bieżącego użytkownika. | Kontrola źródła pakietu VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Ten interfejs jest używany do monitorowania zdarzeń w celu wykonywania operacji, takich jak sprawdzanie w plikach projektu przed zamknięciem rozwiązania lub wprowadzenie nowych plików z kontroli źródła, podczas otwierania projektu. | Kontrola źródła pakietu VSPackage | Zalecane |

## <a name="see-also"></a>Zobacz też
- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)