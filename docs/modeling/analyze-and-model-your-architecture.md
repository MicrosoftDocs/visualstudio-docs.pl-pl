---
title: Analizowanie i modelowanie architektury
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d459f641983960fdd7c4c1ded3b90c0a578c42b3
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873671"
---
# <a name="analyze-and-model-your-architecture"></a>Analizowanie i modelowanie architektury

Upewnij się, że Twoja aplikacja spełnia wymagania dotyczące architektury przy użyciu architektury programu Visual Studio i modelowanie narzędzi do zaprojektowania i modelu aplikacji.

* Łatwiej zrozumieć istniejący kod programu za pomocą programu Visual Studio wizualizować strukturę kodu, zachowanie i relacje.

* Poinformuj zespół na potrzeby troską zależności architektonicznych.

* Twórz modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji w ramach procesu tworzenia aplikacji.

Zobacz [scenariusza: Zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>Zadanie

|||
|-|-|
|**Wizualizacja kodu**:<br /><br /> — Zobacz organizacją i relacje w kodzie przez utworzenie map kodów. Wizualizacja zależności między zestawów, przestrzeni nazw, klas, metod i tak dalej.<br />— Zobacz klasy, struktury i elementy członkowskie dla określonego projektu, tworząc diagramów klas z kodu.<br />-Znajdowanie konfliktów między kodu i jego projekt, tworząc diagramów zależności, aby walidować kod.|-   [Wizualizacja kodu](../modeling/visualize-code.md)<br />-   [Praca z klasami i innymi typami (Projektant klas)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />-   [Wideo: Poznawanie projektu na podstawie kodu dzięki mapom kodu w programie Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Zdefiniuj architektury**:<br /><br /> -Definiowanie i wymuszanie ograniczeń zależności między składnikami kodu przez tworzenie diagramów zależności.|-   [Wideo: Sprawdzanie poprawności architektury zależności za pomocą programu Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Weryfikacja systemu z wymaganiami i przeznaczony projektu:**<br /><br /> — Sprawdzanie poprawności zależności kodu przy użyciu diagramów zależności, które opisują planowaną architekturę i uniemożliwiają zmiany, które mogą powodować konflikty z projektem.|-   [Wideo: Sprawdzanie poprawności architektury zależności za pomocą programu Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Dostosowywanie diagramów i modeli**:<br /><br /> — Utwórz swoje własne języki specyficzne dla domeny.|-   [Modeling SDK for Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generowanie tekstu przy użyciu szablonów T4**:<br /><br /> — Użyj bloków tekstu i logiki formantu wewnątrz szablonów do generowania plików tekstowych.<br /> -T4 szablonów kompilacji za pomocą narzędzia MSBuild zawarte w Visual Studio|-   [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Udostępnianie modeli, diagramy i map kodu za pomocą kontroli wersji serwera Team Foundation**:<br /><br /> — Umieść map kodu, projektów i diagramów zależności w ramach kontroli wersji Team Foundation, dzięki czemu możesz udostępnić je.| |

Aby dowiedzieć się, jakie wersje programu Visual Studio obsługują każdej funkcji, zobacz [obsługę wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Typy modeli i typowe zastosowania

### <a name="code-maps"></a>Mapy kodu
Mapy kodu pomagają zobaczyć organizacją i relacje w kodzie.

**Typowe zastosowania:**

-   Sprawdź kod programu, można lepiej zrozumieć jego strukturę i jego zależności, jak zaktualizować go i oszacować koszt proponowane zmiany.

**Zobacz:**

-   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
-   [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagram"></a>Diagram zależności
Diagramy zależności umożliwiają zdefiniowanie struktury aplikacji jako zestaw warstw lub bloki jawne zależności. Można uruchomić sprawdzania poprawności, aby odnaleźć konfliktów między zależnościami w kodzie i zależności opisane na diagram zależności.

**Typowe zastosowania:**

-   Stabilizowanie struktury aplikacji za pomocą liczne zmiany za pośrednictwem jego użytkowania.
-   Odkryj konflikty niezamierzonych zależności przed zaewidencjonowaniem zmian w kodzie.

**Zobacz:**

-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
-   [Diagramy zależności: informacje](../modeling/layer-diagrams-reference.md)
-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Języka specyficznego dla domeny (DSL)
DSL jest notacji, która projektowania do określonego celu. W programie Visual Studio jest zazwyczaj graficznego.

**Typowe zastosowania:**

-   Generowanie lub skonfigurować części aplikacji. Praca jest wymagany do tworzenia, narzędzia i notacji. Wynik może być lepszym rozwiązaniem niż dostosowywania UML do domeny.
-   W przypadku dużych projektów lub linii produktów, w którym inwestycji w opracowywaniu język DSL i jego narzędzi jest zwracany przez jej użycie w więcej niż jeden projekt.

**Zobacz:**

-   [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?

[Program Visual Studio visualization and Modeling Tools Forum](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>Zobacz także

- [Nowości dotyczące modelowania w programie Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps i zarządzanie cyklem życia aplikacji](/azure/devops/user-guide/devops-alm-overview)
