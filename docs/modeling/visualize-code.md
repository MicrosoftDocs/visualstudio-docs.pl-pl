---
title: Tworzenie wizualizacji kodu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b938321c2b6d1161052ac2358547d72a6bf4e7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593996"
---
# <a name="visualize-code"></a>Tworzenie wizualizacji kodu

Narzędzia do wizualizacji i modelowania w programie Visual Studio ułatwiają zapoznanie się z istniejącym kodem i opisywanie aplikacji. Dzięki temu możesz wzrokowo sprawdzić, jak wprowadzane zmiany mogą wpłynąć na kod, i ocenić nakład pracy oraz zagrożenia związane z tymi zmianami. Na przykład:

- Aby zrozumieć relacje w kodzie, zamapuj je wizualnie.

- Aby opisać architekturę systemu i zachować spójność kodu z projektem, Utwórz diagramy zależności i sprawdź poprawność kodu względem tych diagramów.

- Aby opisać struktury klas, Utwórz diagramy klas.

Te narzędzia ułatwiają również szybkie komunikowanie się z osobami korzystającymi z Twojego projektu.

Aby sprawdzić, które wersje programu Visual Studio obsługują każdą funkcję, zobacz temat [Obsługa architektury i narzędzi modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|||
|-|-|
|**Opis kodu i jego relacji:**<br /><br /> Mapuj relacje między określonymi fragmentami kodu.<br /><br /> Zapoznaj się z omówieniem relacji w kodzie dla całego rozwiązania.|- [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />- [użyć map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Znajdowanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Opis struktur klas:**<br /><br /> Wizualizuj strukturę klas w projekcie, tworząc diagramy klas z kodu.|[Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Opisz projekt systemu wysokiego poziomu i sprawdź poprawność kodu dla tego projektu:**<br /><br /> Opisz projekt systemu wysokiego poziomu i jego zamierzone zależności, tworząc diagramy zależności. Sprawdź poprawność kodu względem tego projektu, aby upewnić się, że zależności w kodzie pozostają spójne z projektem.|- [utworzyć diagramy zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [diagramy zależności: wytyczne](../modeling/layer-diagrams-guidelines.md)<br />- [sprawdzać poprawność kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Zobacz także

- [Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
