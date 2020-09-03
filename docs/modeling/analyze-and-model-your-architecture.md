---
title: Analizowanie i modelowanie architektury
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1db28867ea47752aa74b7898c44e797c0704594
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544225"
---
# <a name="analyze-and-model-your-architecture"></a>Analizowanie i modelowanie architektury

Upewnij się, że Twoja aplikacja spełnia wymagania architektury przy użyciu architektury programu Visual Studio i narzędzi modelowania do projektowania i modelowania aplikacji.

* Łatwiejsze zrozumienie istniejącego kodu programu przy użyciu programu Visual Studio do wizualizacji struktury kodu, zachowania i relacji.

* Poinformuj zespół o konieczności przestrzegania zależności architektonicznych.

* Twórz modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji w ramach procesu tworzenia oprogramowania.

Zobacz [Scenariusz: Zmień projekt przy użyciu wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Dokumentacja artykułu

|Scenariusz|Artykuły|
|-|-|
|**Wizualizuj kod**:<br /><br />— Zobacz temat organizacja i relacje kodu, tworząc mapy kodu. Wizualizuj zależności między zestawami, przestrzeniami nazw, klasami, metodami i tak dalej.<br />-Zobacz strukturę klas i składowe dla określonego projektu, tworząc diagramy klas z kodu.<br />— Znajdź konflikty między kodem i jego projektem, tworząc diagramy zależności do walidacji kodu.|- [Wizualizuj kod](../modeling/visualize-code.md)<br />- [Praca z klasami i innymi typami (Projektant klas)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [Wideo: zrozumienie projektu na podstawie kodu za pomocą map kodu programu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [Wideo: Weryfikuj zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Zdefiniuj architekturę**:<br /><br />-Definiowanie i wymuszanie ograniczeń zależności między składnikami kodu przez tworzenie diagramów zależności.|- [Wideo: weryfikowanie zależności architektury za pomocą programu Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Sprawdź, czy system spełnia wymagania i zamierzony projekt:**<br /><br />-Weryfikuj zależności kodu przy użyciu diagramów zależności, które opisują zamierzoną architekturę i zapobiegają zmianom, które mogą powodować konflikty z projektem.|- [Wideo: weryfikowanie zależności architektury za pomocą programu Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Dostosuj modele i diagramy**:<br /><br />— Tworzenie własnych języków specyficznych dla domeny.|- [Modeling SDK dla programu Visual Studio — Języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generuj tekst przy użyciu szablonów T4**:<br /><br />-Używaj bloków tekstowych i logiki formantów wewnątrz szablonów do generowania plików tekstowych.<br /> — Kompilacja szablonów T4 z użyciem MSBuild w programie Visual Studio|- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Udostępnianie modeli, diagramów i map kodu przy użyciu kontroli wersji programu Team Foundation**:<br /><br />— Umieść mapy kodu, projekty i diagramy zależności w ramach kontroli wersji programu Team Foundation, aby można było je udostępnić.| |

Aby sprawdzić, które wersje programu Visual Studio obsługują każdą funkcję, zobacz temat [Obsługa architektury i narzędzi modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Typy modeli i typowe zastosowania

### <a name="code-maps"></a>Mapy kodu

Mapy kodu pomagają zobaczyć organizację i relacje w kodzie.

**Typowe zastosowania:**

- Badaj kod programu, aby lepiej zrozumieć jego strukturę i jej zależności, jak go zaktualizować, i oszacować koszt proponowanych zmian.

**Wyświetlania**

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Diagramy zależności

Diagramy zależności pozwalają definiować strukturę aplikacji jako zestaw warstw lub bloków z jawnymi zależnościami. Walidacja na żywo pokazuje konflikty między zależnościami w kodzie i zależnościami opisanymi na diagramie zależności.

**Typowe zastosowania:**

- Stabilizacja struktury aplikacji dzięki licznym zmianom w jego życiu.
- Odkryj nieumyślne konflikty zależności przed zaewidencjonowaniem zmian w kodzie.

**Wyświetlania**

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Język specyficzny dla domeny (DSL)

DSL to notacja, którą można zaprojektować w określonym celu. W programie Visual Studio jest zwykle graficzny.

**Typowe zastosowania:**

- Generuj lub Konfiguruj części aplikacji. Do opracowania notacji i narzędzi wymagane jest działanie. Wynik może być lepszym dopasowaniem do domeny niż dostosowanie UML.
- W przypadku dużych projektów lub w wierszach produktu, w których inwestycje w programowanie DSL i jej narzędzia są zwracane przez użycie w więcej niż jednym projekcie.

**Wyświetlania**

- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Zobacz też

- [Nowości dotyczące modelowania w programie Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps i zarządzanie cyklem życia aplikacji](/azure/devops/user-guide/devops-alm-overview)
