---
title: Powiązane usługi i interfejsy (pakiet VSPackage kontroli kodu źródłowego)
titleSuffix: ''
description: Dowiedz się więcej o interfejsach związanych z pakietem VSPackage kontroli źródła w zestawie SDK Visual Studio SDK. Pakiet implementuje niektóre interfejsy i używa innych do kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6385307c91541204d58228b489160888f79dec85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903336"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Powiązane usługi i interfejsy (pakiet VSPackage kontroli kodu źródłowego)

W tej sekcji wymieniono wszystkie interfejsy związane z pakietem VSPackage kontroli źródła w pliku [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Pakiet VSPackage kontroli źródła implementuje niektóre z tych interfejsów i używa innych do wykonywania zadań kontroli źródła.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfejsy implementowane przez i dla pakietów VSPackage kontroli kodu źródłowego

 Poniższe interfejsy są opisane w pliku , a pakiet VSPackage kontroli źródła implementuje ich podzestaw [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] w zależności od żądanego zestawu funkcji. Niektóre interfejsy są oznaczone jako wymagane i muszą być implementowane przez każdy pakiet VSPackage kontroli źródła.

 Dla tych interfejsów, których pakiet nie implementuje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] program zapewnia implementację domyślną. Należy pamiętać, że domyślna implementacja jest przeznaczona dla przypadków, gdy żaden pakiet VSPackage nie jest zarejestrowany i żaden projekt nie jest kontrolowany. Poprawnie napisany pakiet VSPackage kontroli źródła implementuje wszystkie niezbędne interfejsy, zamiast pozostawiać je w domyślnej implementacji tych interfejsów.

 Pakiet VSPackage kontroli źródła musi implementować usługę prywatną, która hermetyzuje niektóre lub wszystkie poniższe interfejsy.

 Interfejsy są:

- Wymagane: odpowiednia jednostka (pakiet VSPackage kontroli źródła, wycinki kontroli kodu źródłowego, projekt) musi implementować interfejs.

- Zalecane: jednostka powinna implementować ten interfejs; W przeciwnym razie funkcjonalność kontroli źródła może być ograniczona.

- Opcjonalnie: jednostka może zaimplementować ten interfejs, aby zapewnić bogatszy zestaw funkcji.

| Interfejs | Przeznaczenie | Zaimplementowane przez | Zaimplementować? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Edytory wywołują ten interfejs przed zmodyfikowaniem lub zapisaniem pliku. Pakiet VSPackage kontroli źródła może wyewidencjonować plik lub odmówić operacji w przypadku niepowodzenia wyewidencjonowania. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Ten interfejs zapewnia podstawowe funkcje kontroli źródła dla projektów, takie jak rejestrowanie i wyrejestrowanie projektów z kontrolą źródła oraz zapewnia obsługę podstawowych glifów kontroli źródła. | Pakiet VSPackage kontroli kodu źródłowego | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Ten interfejs jest uzyskiwany z obiektu przy użyciu funkcji lub przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> rzutowanie obiektu implementowania `IVsHierarchy` na `IVsSccProject2` . Służy do uzyskiwania plików pod kontrolą źródła w projekcie lub do informowania projektu o bieżącym stanie lub lokalizacji kontroli źródła. | Project | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Moduł integracji używa tego interfejsu do ustawienia bieżącego aktywnego pakietów VSPackage. | Pakiet VSPackage kontroli kodu źródłowego | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Ten interfejs jest oparty na modelu subskrypcji. Każdy pakiet VSPackage może zasygnalizować, że chce odbierać zdarzenia dotyczące dokumentów, i być poinformowany przez powłokę o zdarzeniach, które mają się zdarzyć. Jest on implementowany i obsługiwany przez program , który z kolei przekazuje zdarzenia implementujące pakiet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] `IVsTrackProjectDocumentsEvents2` do vspackage. | Wycinki kontroli kodu źródłowego | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Ten interfejs zapewnia przetwarzanie wsadowe, zsynchronizowane operacje odczytu/zapisu oraz zaawansowaną `OnQueryAddFiles` metodę. | Wycinki kontroli kodu źródłowego | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Eksplorator rozwiązań** i projekty wywołują ten interfejs, gdy nowe pliki są dodawane do projektów lub gdy nazwy plików i folderów są zmieniane lub usuwane z projektów. Pakiet VSPackage kontroli źródła może wyewidencjiować plik projektu lub anulować operację. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Eksplorator rozwiązań** i projekty wywołują ten interfejs w odpowiedzi na wywołania metod interfejsu IVstrackProjectDocuments3. Pakiet VSPackage kontroli źródła może śledzić operacje wsadowe, synchronizować operacje odczytu/zapisu i pracować z bardziej zaawansowaną `OnQueryAddFiles` metodą. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Ten interfejs zapewnia obsługę zarządzania listą dla projektów internetowych. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Ten interfejs służy do pobierania etykietek narzędzi dla plików kontrolowanych przez źródło w projektach. | Pakiet VSPackage kontroli kodu źródłowego | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Ten interfejs zapewnia obsługę rozszerzenia przestrzeni nazw. | Pakiet VSPackage kontroli kodu źródłowego | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Pakiet VSPackage używa tego interfejsu do integracji rozszerzenia przestrzeni nazw z oknami **dialogowymi Nowy,** **Otwórz** **lub** Zapisz. W związku z tym projekty mogą być automatycznie dodawane do kontroli źródła podczas tworzenia lub dodawane do kontroli źródła, gdy operacja zapisywania jest w mocy. | Pakiet VSPackage kontroli kodu źródłowego | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Pakiet VSPackage używa tego interfejsu do definiowania dodatkowych glifów jako glifów kontroli źródła dla węzłów w **Eksplorator rozwiązań**. | Pakiet VSPackage kontroli kodu źródłowego | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Ten **interfejs** jest używany w oknie dialogowym Dodawanie projektów internetowych. Udostępnia on metody przeglądania dla lokalizacji kontroli źródła i otwierania projektu internetowego wcześniej dodanego w repozytorium kontroli źródła w tej lokalizacji. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Ten interfejs zapewnia obsługę asynchronicznego ładowania projektów (w tle) z kontroli źródła. | Pakiet VSPackage kontroli kodu źródłowego | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Ten interfejs umożliwia projektom obserwowanie postępu ładowania asynchronicznego zainicjowanego przez program <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Ten interfejs umożliwia ideom wykonywanie zapytań względem aktywnego pakietu VSPackage kontroli źródła. Ide wysyła zapytanie o wartość ustawień kontroli źródła, które mają znaczenie nawet wtedy, gdy nie ma zarejestrowanego aktywnego pliku VSPackage kontroli źródła. Ten interfejs jest implementowany i obsługiwany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Wycinki kontroli kodu źródłowego | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Ten interfejs jest używany do rejestrowania pakietów VSPackage kontroli źródła. | Wycinki kontroli kodu źródłowego | Wymagane |
| <xref:EnvDTE.SourceControl> | Ten interfejs jest używany w automatyzacji. W związku z tym uwidacznia tylko funkcje, które mogą być wykonywane bez wyświetlania żadnego interfejsu użytkownika. | Pakiet VSPackage kontroli kodu źródłowego | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Ten interfejs służy do zapisywania ustawień kontroli źródła w pliku rozwiązania (sln). Ustawienia obejmują lokalizację kontroli źródła i flagi stanu kontroli źródła. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Ten interfejs służy do zapisywania ustawień kontroli źródła w pliku opcji rozwiązania (suo). Może to obejmować ustawienia kontroli źródła specyficzne dla użytkownika, takie jak lokalizacja enlistment bieżącego użytkownika. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Ten interfejs służy do monitorowania zdarzeń w celu wykonywania operacji, takich jak sprawdzanie plików projektu przed zamknięciem rozwiązań lub pobieranie nowych plików z kontroli źródła podczas otwierania projektu. | Pakiet VSPackage kontroli kodu źródłowego | Zalecane |

## <a name="see-also"></a>Zobacz też
- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
