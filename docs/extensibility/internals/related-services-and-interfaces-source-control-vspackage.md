---
title: Powiązane usługi i interfejsy (Kontrola źródła VSPackage) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705625"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Powiązane usługi i interfejsy (pakiet VSPackage kontroli kodu źródłowego)
W tej sekcji wymieniono wszystkie interfejsy związane [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]z formantu źródła VSPackage w pliku . Formant źródła VSPackage implementuje niektóre z tych interfejsów i używa innych do wykonywania zadań kontroli źródła.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfejsy implementowane przez i dla kontroli źródła VSPackages
 Następujące interfejsy są opisane [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]w programie , a formant źródłowy VSPackage implementuje ich podzbiór w zależności od żądanego zestawu funkcji. Niektóre interfejsy są oznaczone jako wymagane i muszą być zaimplementowane przez każdego formantu źródła VSPackage.

 Dla tych interfejsów, które pakiet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie implementuje, zapewnia domyślną implementację. Należy zauważyć, że domyślna implementacja jest przeznaczona dla przypadku, gdy nie VSPackage jest zarejestrowany i żaden projekt jest kontrolowany. Poprawnie napisany formant źródła VSPackage implementuje wszystkie niezbędne interfejsy, zamiast pozostawiać go domyślnej implementacji tych interfejsów.

 Formant źródła VSPackage należy zaimplementować usługę prywatną, która hermetyzuje niektóre lub wszystkie z następujących interfejsów.

 Interfejsy to:

- Wymagane: Odpowiednia jednostka (kontrola źródła VSPackage, Source Control Stub, projekt) musi implementować interfejs.

- Zalecane: Jednostka powinna zaimplementować ten interfejs; w przeciwnym razie funkcja kontroli źródła może być ograniczona.

- Opcjonalnie: jednostka może zaimplementować ten interfejs, aby zapewnić bogatszy zestaw funkcji.

| Interface | Przeznaczenie | Zaimplementowane przez | Zaimplementować? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Edytorzy nazywają ten interfejs przed zmodyfikowaniem lub zapisaniem pliku. Formant źródła VSPackage można wyewidencjonować plik lub odmówić operacji, jeśli wyewidencjonowanie nie powiedzie się. | Kontrola źródła VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Ten interfejs zapewnia podstawowe funkcje kontroli źródła dla projektów, takich jak rejestrowanie i wyrejestrowywanie projektów z kontrolą źródła i zapewnienie obsługi podstawowych glifów kontroli źródła. | Kontrola źródła VSPackage | Wymagany |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Ten interfejs jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> uzyskiwany z funkcji za <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> pomocą `IVsHierarchy` `IVsSccProject2`lub po prostu rzutowanie obiektu implementacji do . Służy do uzyskiwania plików pod kontrolą źródła w projekcie lub do informowania projektu o bieżącym stanie lub lokalizacji kontroli źródła. | Projekt | Wymagany |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Moduł integracji używa tego interfejsu, aby ustawić bieżący aktywny VSPackage. | Kontrola źródła VSPackage | Wymagany |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Ten interfejs jest oparty na modelu subskrypcji. Każdy VSPackage może sygnalizować, że chce odbierać zdarzenia dokumentu i być zalecane przez powłoki na zdarzenia, które mają się zdarzyć. Jest zaimplementowana [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]i obsługiwana przez , `IVsTrackProjectDocumentsEvents2` który z kolei przekazuje zdarzenia implementujące do VSPackage. | Odcinek kontroli źródła | Wymagany |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Ten interfejs zapewnia przetwarzanie wsadowe, zsynchronizowane operacje odczytu/zapisu oraz metodę zaawansowaną. `OnQueryAddFiles` | Odcinek kontroli źródła | Wymagany |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Eksplorator rozwiązań** i projekty wywołują ten interfejs, gdy nowe pliki są dodawane do projektów lub gdy nazwy plików i folderów są zmieniane lub usuwane z projektów. Formant źródła VSPackage można wyewidencjonować plik projektu lub anulować operację. | Kontrola źródła VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Eksplorator rozwiązań** i projekty wywołać ten interfejs w odpowiedzi na wywołania do metod interfejsu IVstrackProjectDocuments3. Formant źródła VSPackage może śledzić operacje wsadowe, zsynchronizowane operacje odczytu/zapisu i pracować z bardziej zaawansowaną `OnQueryAddFiles` metodą. | Kontrola źródła VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Ten interfejs zapewnia obsługę zarządzania rekrutacją dla projektów sieci Web. | Kontrola źródła VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Ten interfejs służy do pobierania etykietek narzędzi dla plików kontrolowanych przez źródło w projektach. | Kontrola źródła VSPackage | Optional (Opcjonalność) |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Ten interfejs zapewnia obsługę rozszerzenia obszaru nazw. | Kontrola źródła VSPackage | Optional (Opcjonalność) |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Program VSPackage używa tego interfejsu do zintegrowania rozszerzenia obszaru nazw z oknami dialogowymi **Nowe**, **Otwórz**lub **Zapisz.** W związku z tym projekty mogą być automatycznie dodawane do kontroli źródła podczas tworzenia lub dodawane do kontroli źródła, gdy operacja zapisywania jest w życie. | Kontrola źródła VSPackage | Optional (Opcjonalność) |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage używa tego interfejsu do definiowania dodatkowych glifów jako glifów kontroli źródła dla węzłów w **Eksploratorze rozwiązań**. | Kontrola źródła VSPackage | Optional (Opcjonalność) |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Okno dialogowe **Dodawanie** dla projektów sieci Web używa tego interfejsu. Udostępnia metody przeglądania lokalizacji kontroli źródła i otwierania projektu sieci Web wcześniej dodane w repozytorium kontroli źródła w tej lokalizacji. | Kontrola źródła VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Ten interfejs zapewnia obsługę ładowania asynchronii (w tle) projektów z kontroli źródła. | Kontrola źródła VSPackage | Optional (Opcjonalność) |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Ten interfejs umożliwia projektom obserwowanie postępu ładowania asynchroniiowego zainicjowanego przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>program . | Projekt | Optional (Opcjonalność) |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Ten interfejs umożliwia IDE do kwerendy active source control VSPackage. IDE odpytywa wartość ustawień kontroli źródła, które mają znaczenie nawet wtedy, gdy nie ma aktywnego formantu źródła VSPackage zarejestrowany. Ten interfejs jest zaimplementowany i obsługiwany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. | Odcinek kontroli źródła | Wymagany |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Ten interfejs jest używany do rejestrowania formantu źródła VSPackage. | Odcinek kontroli źródła | Wymagany |
| <xref:EnvDTE.SourceControl> | Ten interfejs jest używany w automatyzacji. W związku z tym udostępnia tylko funkcje, które mogą być wykonywane bez wyświetlania interfejsu użytkownika. | Kontrola źródła VSPackage | Optional (Opcjonalność) |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Ten interfejs służy do zapisywania ustawień kontroli źródła w pliku rozwiązania (.sln). Ustawienia obejmują flagi lokalizacji kontroli źródła i stanu kontroli źródła. | Kontrola źródła VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Ten interfejs służy do zapisywania ustawień kontroli źródła w pliku opcji rozwiązania (.suo). Może to obejmować ustawienia kontroli źródła specyficzne dla użytkownika, takie jak bieżąca lokalizacja rejestracji użytkownika. | Kontrola źródła VSPackage | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Ten interfejs służy do monitorowania zdarzeń w celu wykonywania operacji, takich jak sprawdzanie plików projektu przed zamknięciem rozwiązań lub uzyskiwanie nowych plików z kontroli źródła podczas otwierania projektu. | Kontrola źródła VSPackage | Zalecane |

## <a name="see-also"></a>Zobacz też
- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
