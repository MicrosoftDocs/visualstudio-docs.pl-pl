---
title: Architektura wtyczki kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705107"
---
# <a name="source-control-plug-in-architecture"></a>Architektura wtyczki kontroli kodu źródłowego
Można dodać obsługę kontroli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] źródła do zintegrowanego środowiska programistycznego (IDE) przez implementowanie i podłączanie wtyczki kontroli źródła. IDE łączy się z wtyczką kontroli źródła za pośrednictwem dobrze zdefiniowanego interfejsu API wtyczki kontroli źródła. IDE udostępnia funkcje kontroli wersji systemu kontroli źródła, zapewniając interfejs użytkownika (UI), który składa się z pasków narzędzi i poleceń menu. Wtyczka kontroli źródła implementuje funkcje kontroli źródła.

## <a name="source-control-plug-in-resources"></a>Zasoby wtyczki kontroli źródła
 Wtyczka kontroli źródła udostępnia zasoby ułatwiające tworzenie i łączenie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikacji do przechowywania wersji z ideą. Wtyczka kontroli źródła zawiera specyfikację interfejsu API, która musi zostać zaimplementowana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wtyczkę kontroli źródła, aby można ją było zintegrować z IDE. Zawiera również przykładowy kod (napisany w języku C++), który implementuje wtyczkę kontroli źródła szkieletu demonstrując implementację podstawowych funkcji zgodnych z interfejsem API wtyczki kontroli źródła.

 Specyfikacja interfejsu API wtyczki source control umożliwia korzystanie z dowolnego wybranego systemu kontroli źródła, jeśli utworzysz bibliotekę DLL kontroli źródła z wymaganym zestawem funkcji zaimplementowanych zgodnie z interfejsem API wtyczki kontroli źródła.

## <a name="components"></a>Składniki
 Pakiet karty kontroli źródła na diagramie jest składnikiem IDE, który tłumaczy żądanie użytkownika dla operacji kontroli źródła na wywołanie funkcji obsługiwane przez wtyczkę kontroli źródła. Aby tak się stało, IDE i wtyczki kontroli źródła musi mieć skuteczne okno dialogowe, które przekazuje informacje tam iz powrotem między IDE i wtyczki. Aby to okno dialogowe miało miejsce, obaj muszą mówić tym samym językiem. Interfejs API wtyczki kontroli źródła opisany w tej dokumentacji jest wspólne słownictwo dla tej wymiany.

 ![Diagram architektury kontroli kodu źródłowego](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagram architektury przedstawiający interakcję między wtyczką vs i wtyczką kontroli źródła

 Jak pokazano na diagramie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architektury, powłoka, oznaczona jako powłoka VS na diagramie, zawiera działające projekty użytkownika i skojarzone składniki, takie jak edytory i Eksplorator rozwiązań. Pakiet karty kontroli źródła obsługuje interakcję między IDE i wtyczki kontroli źródła. Pakiet karty kontroli źródła zapewnia własny interfejs użytkownika kontroli źródła. Jest to interfejs użytkownika najwyższego poziomu, z którymi użytkownik współdziała w celu zainicjowania i zdefiniowania zakresu operacji kontroli źródła.

 Wtyczka kontroli źródła może mieć własny interfejs użytkownika, który może składać się z dwóch części, jak pokazano na rysunku. Pole oznaczone jako "Interfejs użytkownika dostawcy" reprezentuje niestandardowe elementy interfejsu użytkownika, które udostępniasz jako twórca wtyczki kontroli źródła. Są one wyświetlane bezpośrednio przez wtyczkę kontroli źródła, gdy użytkownik wywołuje operację zaawansowanego sterowania źródłem. Pole oznaczone jako "Helper UI" jest zestawem funkcji interfejsu użytkownika wtyczki kontroli źródła, które są pośrednio wywoływane za pośrednictwem IDE. Wtyczka kontroli źródła przekazuje komunikaty związane z interfejsem użytkownika do IDE za pośrednictwem specjalnych funkcji wywołania zwrotnego dostarczonych przez IDE. Interfejs użytkownika pomocnika ułatwia bardziej bezproblemową integrację z IDE (często za pomocą przycisku **Zaawansowane)** i w ten sposób zapewnia bardziej ujednolicone środowisko użytkownika końcowego.

 Wtyczka kontroli źródła nie może [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wprowadzać zmian w powłoce i, w związku z tym, do pakietu karty kontroli źródła lub interfejsu użytkownika kontroli źródła dostarczonych przez IDE. Musi maksymalnie wykorzystać elastyczność oferowaną poprzez implementację różnych funkcji interfejsu API wtyczki kontroli źródła, które przyczyniają się do zintegrowanego środowiska dla użytkownika końcowego. Sekcja referencyjna dokumentacji interfejsu API wtyczki source control zawiera informacje dotyczące niektórych zaawansowanych funkcji wtyczki kontroli źródła. Aby wykorzystać te funkcje, wtyczka kontroli źródła musi zadeklarować swoje zaawansowane możliwości do IDE podczas inicjowania i musi implementować określone zaawansowane funkcje dla każdej funkcji.

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)
- [Słownik](../../extensibility/source-control-plug-in-glossary.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)
