---
title: Powiązane usługi i interfejsy (pakiet VSPackage kontroli kodu źródłowego)
titleSuffix: ''
description: Dowiedz się więcej o interfejsie związanym z pakietu VSPackage kontroli źródła w zestawie SDK programu Visual Studio. Pakiet implementuje niektóre interfejsy i używa innych do kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f35a11c801a8535c2b903909e2514b9879d3347c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095033"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Powiązane usługi i interfejsy (pakiet VSPackage kontroli kodu źródłowego)

W tej sekcji znajduje się lista wszystkich interfejsów pakietu VSPackage związanych z kontrolą źródła w programie [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Pakietu VSPackage kontroli źródła implementuje niektóre z tych interfejsów i używa innych do wykonywania zadań kontroli źródła.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfejsy zaimplementowane przez i dla pakietów VSPackage kontroli źródła

 Poniższe interfejsy są opisane w [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , a pakietu VSPackage kontroli źródła implementuje podzestaw z nich w zależności od żądanego zestawu funkcji. Niektóre interfejsy są oznaczone jako wymagane i muszą być zaimplementowane przez każdy pakietu VSPackage kontroli źródła.

 Dla tych interfejsów, których pakiet nie implementuje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zapewnia implementację domyślną. Należy zauważyć, że domyślna implementacja została zaprojektowana dla przypadku, gdy nie zarejestrowano żadnych pakietu VSPackage i żaden projekt nie jest kontrolowany. Prawidłowo zapisywana kontrola źródła pakietu VSPackage implementuje wszystkie niezbędne interfejsy, a nie opuszcza go do domyślnej implementacji tych interfejsów.

 Pakietu VSPackage kontroli źródła musi implementować usługę prywatną, która hermetyzuje niektóre lub wszystkie z następujących interfejsów.

 Interfejsy są:

- Wymagane: odpowiednia jednostka (pakietu VSPackage kontroli źródła, Klasa zastępcza kontroli źródła, projekt) musi implementować interfejs.

- Zalecane: jednostka powinna zaimplementować ten interfejs; w przeciwnym razie funkcje kontroli źródła mogą być ograniczone.

- Opcjonalnie: jednostka może zaimplementować ten interfejs, aby zapewnić bogatszy zestaw funkcji.

| Interfejs | Przeznaczenie | Zaimplementowane przez | Wprowadzą? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Edytory wywołują ten interfejs Przed zmodyfikowaniem lub zapisaniem pliku. Pakietu VSPackage kontroli źródła może wyewidencjonować plik lub odrzucić operację, jeśli wyewidencjonowanie nie powiedzie się. | Pakietu VSPackage kontroli źródła | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Ten interfejs zapewnia podstawowe funkcje kontroli źródła dla projektów, takie jak rejestrowanie i Wyrejestrowywanie projektów z kontrolą źródła i zapewnianie pomocy technicznej dla podstawowych symboli kontroli źródła. | Pakietu VSPackage kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Ten interfejs jest uzyskiwany z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> użycia <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funkcji lub przez po prostu rzutowanie obiektu implementującego `IVsHierarchy` na `IVsSccProject2` . Służy do pobierania plików pod kontrolą źródła w projekcie lub do informowania projektu bieżącego stanu lub lokalizacji kontroli źródła. | Project | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | Moduł integracji używa tego interfejsu do ustawienia bieżącego aktywnego pakietu VSPackage. | Pakietu VSPackage kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Ten interfejs jest oparty na modelu subskrypcji. Każdy pakietu VSPackage może sygnalizować, że chce otrzymywać zdarzenia dokumentu i polecić powłokę w przypadku zdarzeń, które się zdarzają. Jest zaimplementowany i obsługiwany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , co z kolei powoduje przekazanie zdarzeń implementujących `IVsTrackProjectDocumentsEvents2` do pakietu VSPackage. | Procedura wejścia kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Ten interfejs zapewnia przetwarzanie wsadowe, synchronizowane operacje odczytu/zapisu oraz zaawansowaną `OnQueryAddFiles` metodę. | Procedura wejścia kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Eksplorator rozwiązań** i projekty wywołują ten interfejs po dodaniu nowych plików do projektów lub po zmianie nazwy plików i folderów lub usunięciu ich z projektów. Pakietu VSPackage kontroli źródła może wyewidencjonować plik projektu lub anulować operację. | Pakietu VSPackage kontroli źródła | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Eksplorator rozwiązań** i projekty wywołują ten interfejs w odpowiedzi na wywołania metod interfejsu IVstrackProjectDocuments3. Pakietu VSPackage kontroli źródła może śledzić operacje wsadowe, synchronizować operacje odczytu i zapisu oraz korzystać z bardziej zaawansowanej `OnQueryAddFiles` metody. | Pakietu VSPackage kontroli źródła | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Ten interfejs zapewnia obsługę zarządzania rejestracją dla projektów sieci Web. | Pakietu VSPackage kontroli źródła | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Ten interfejs służy do pobierania etykietek narzędzi dla plików kontrolowanych przez źródło w projektach. | Pakietu VSPackage kontroli źródła | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Ten interfejs zapewnia obsługę rozszerzenia przestrzeni nazw. | Pakietu VSPackage kontroli źródła | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | Pakietu VSPackage używa tego interfejsu do integrowania rozszerzenia przestrzeni nazw w oknach dialogowych **Nowy**, **Otwórz** lub **Zapisz** . W związku z tym projekty mogą być automatycznie dodawane do kontroli źródła podczas tworzenia lub dodawane do kontroli źródła, gdy trwa operacja zapisywania. | Pakietu VSPackage kontroli źródła | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | Pakietu VSPackage używa tego interfejsu, aby zdefiniować dodatkowe glify jako glify kontroli źródła dla węzłów w **Eksplorator rozwiązań**. | Pakietu VSPackage kontroli źródła | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | Okno dialogowe **Dodawanie** dla projektów sieci Web używa tego interfejsu. Zapewnia metody przeglądania w poszukiwaniu lokalizacji kontroli źródła i otwierania projektu sieci Web, który został wcześniej dodany w repozytorium kontroli źródła w tej lokalizacji. | Pakietu VSPackage kontroli źródła | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Ten interfejs zapewnia obsługę asynchronicznego (w tle) ładowania projektów z kontroli źródła. | Pakietu VSPackage kontroli źródła | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Ten interfejs umożliwia projektom oglądanie postępu asynchronicznego ładowania zainicjowane przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Ten interfejs umożliwia IDE zapytania o aktywny pakietu VSPackage kontroli źródła. IDE wysyła zapytanie do wartości ustawień kontroli źródła, które mają znaczenie nawet wtedy, gdy nie ma żadnych zarejestrowanych aktywnych kontroli źródła pakietu VSPackage. Ten interfejs jest zaimplementowany i obsługiwany przez program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Procedura wejścia kontroli źródła | Wymagane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Ten interfejs jest używany podczas rejestrowania pakietu VSPackage kontroli źródła. | Procedura wejścia kontroli źródła | Wymagane |
| <xref:EnvDTE.SourceControl> | Ten interfejs jest używany w automatyzacji. W związku z tym uwidacznia tylko funkcje, które mogą być wykonywane bez wyświetlania interfejsu użytkownika. | Pakietu VSPackage kontroli źródła | Opcjonalne |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Ten interfejs służy do zapisywania ustawień kontroli źródła w pliku rozwiązania (. sln). Te ustawienia obejmują lokalizację kontroli źródła i flagi stanu kontroli źródła. | Pakietu VSPackage kontroli źródła | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Ten interfejs służy do zapisywania ustawień kontroli źródła w pliku opcji rozwiązania (. suo). Może to dotyczyć specyficznych dla użytkownika ustawień kontroli źródła, takich jak lokalizacja rejestracji bieżącego użytkownika. | Pakietu VSPackage kontroli źródła | Zalecane |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Ten interfejs służy do monitorowania zdarzeń w celu wykonywania operacji, takich jak Ewidencjonowanie plików projektu przed zamknięciem rozwiązań lub pobieranie nowych plików z kontroli źródła podczas otwierania projektu. | Pakietu VSPackage kontroli źródła | Zalecane |

## <a name="see-also"></a>Zobacz też
- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
