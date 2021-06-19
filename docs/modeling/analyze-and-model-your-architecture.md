---
title: Narzędzia do modelowania & architektury
description: Zaprojektuj i modeluj aplikację, aby upewnić się, że spełnia ona wymagania dotyczące architektury.
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542b74e7d3bb73847303fa4215651eea7e110e91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384879"
---
# <a name="analyze-and-model-your-architecture"></a>Analizowanie i modelowanie architektury

Upewnij się, że aplikacja spełnia wymagania dotyczące architektury, Visual Studio architektury i narzędzi modelowania do projektowania i modelowania aplikacji.

1. Lepiej poznaj istniejący kod programu, [wizualizując strukturę,](visualize-code.md) zachowanie i relacje kodu za pomocą map kodu i diagramów zależności.
    - Zobacz organizację i relacje kodu, tworząc **mapy kodu**. 
    - Wizualizowanie zależności między zestawami, przestrzeniami nazw, klasami, metodami itp.
    - Znajdź konflikty między kodem i jego projektem, tworząc **diagramy zależności w** celu zweryfikowania kodu.
    - Zobacz strukturę klas i składowe dla określonego projektu, tworząc [diagramy klas z kodu](../ide/class-designer/designing-and-viewing-classes-and-types.md).
    - [Generuj tekst przy użyciu szablonów T4](../modeling/code-generation-and-t4-text-templates.md) z blokami tekstowym i kontroluj logikę wewnątrz szablonów w celu generowania plików tekstowych. 
    
1. Udziel zespołowi edukacji dotyczącej konieczności przestrzegania zależności architektonicznych.

1. Twórz modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji w ramach procesu tworzenia aplikacji.

Zobacz [Scenariusz: zmienianie projektu przy użyciu wizualizacji i modelowania.](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)

## <a name="code-maps"></a>Mapy kodu

Mapy kodu to jeden z typów modelu, który pomaga zobaczyć organizację i relacje w kodzie.

Użyj map do zbadania kodu programu, aby lepiej zrozumieć jego strukturę i zależności, sposób jego aktualizowania oraz oszacować koszt proponowanych zmian.

Więcej informacji:
- [Instalowanie narzędzi kodu architektury](install-architecture-tools.md)
- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>Diagramy zależności

Diagramy zależności umożliwiają definiowanie struktury aplikacji jako zestawu warstw lub bloków z jawnymi zależnościami. Walidacja na żywo pokazuje konflikty między zależnościami w kodzie i zależnościami opisanymi na diagramie zależności.

Użyj diagramów zależności, aby: 
- Ustabilizowanie struktury aplikacji przez wiele zmian w ciągu swojego życia.
- Wykrywanie niezamierzonych konfliktów zależności przed zaeznawaniem zmian w kodzie.

Więcej informacji:
- [Instalowanie narzędzi kodu architektury](install-architecture-tools.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>Modele języka specyficznego dla domeny (DSL)

DSL to notacja, która jest projektowana do określonego celu. W Visual Studio jest zwykle graficzne.

Użyj języka specyficznego dla domeny, aby: 
- Generowanie lub konfigurowanie części aplikacji. Do opracowania notacji i narzędzi wymagana jest praca. Wynik może być lepiej dopasowany do Twojej domeny niż dostosowanie UML.
- W przypadku dużych projektów lub linii produktów, w których inwestycja w opracowywanie DSL i jego narzędzi jest zwracana przez użycie w więcej niż jednym projekcie.

Więcej informacji:
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa wersji dla architektury i narzędzi do modelowania

Visual Studio jest dostępna w kilku wersjach. Nie wszystkie z nich zapewniają obsługę architektury i narzędzi do modelowania. W poniższej tabeli przedstawiono dostępność każdego narzędzia.

|**Funkcja**|**Wersja Enterprise**|**Wersja Professional**|**Community Edition**|
|-|-|-|-|
|**Mapy kodu**|Tak|Obsługuje tylko odczytywanie map kodu, filtrowanie map kodu, dodawanie nowych węzłów ogólnych i tworzenie nowego wykresu skierowanego z zaznaczenia.|-|
|**Diagramy zależności**|Tak|Obsługuje tylko odczytywanie diagramów zależności.|Obsługuje tylko odczytywanie diagramów zależności.|
|**Wykresy skierowane** (diagramy DGML)|Tak|Tak|Tak|
|**Klonowanie kodu**|Tak|-|-|
