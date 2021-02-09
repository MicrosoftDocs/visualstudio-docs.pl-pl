---
title: Tworzenie wizualizacji kodu
description: Dowiedz się, jak za pomocą narzędzi do wizualizacji i modelowania w programie Visual Studio poznać istniejący kod i opisać swoją aplikację.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a261589af027c76708a70631426d8033eb2ada63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924236"
---
# <a name="visualize-code"></a>Tworzenie wizualizacji kodu

Narzędzia do wizualizacji i modelowania w programie Visual Studio ułatwiają zapoznanie się z istniejącym kodem i opisywanie aplikacji. Dzięki temu można wizualnie dowiedzieć się, jak zmiany mogą wpływać na kod i pomóc w ocenie pracy i zagrożeń wynikających z tych zmian. Na przykład:

- Aby zrozumieć relacje w kodzie, zamapuj je wizualnie.

- Aby opisać architekturę systemu i zachować spójność kodu z projektem, Utwórz diagramy zależności i sprawdź poprawność kodu względem tych diagramów.

- Aby opisać struktury klas, Utwórz diagramy klas.

Te narzędzia ułatwiają również szybkie komunikowanie się z osobami korzystającymi z Twojego projektu.

Aby sprawdzić, które wersje programu Visual Studio obsługują każdą funkcję, zobacz temat [Obsługa architektury i narzędzi modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|Scenariusz|Artykuły|
|-|-|
|**Opis kodu i jego relacji:**<br /><br /> Mapuj relacje między określonymi fragmentami kodu.<br /><br /> Zapoznaj się z omówieniem relacji w kodzie dla całego rozwiązania.|- [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Znajdowanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Mapuj metody na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Opis struktur klas:**<br /><br /> Wizualizuj strukturę klas w projekcie, tworząc diagramy klas z kodu.|[Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Opisz projekt systemu wysokiego poziomu i sprawdź poprawność kodu dla tego projektu:**<br /><br /> Opisz projekt systemu wysokiego poziomu i jego zamierzone zależności, tworząc diagramy zależności. Sprawdź poprawność kodu względem tego projektu, aby upewnić się, że zależności w kodzie pozostają spójne z projektem.|- [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Sprawdzanie poprawności kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Zobacz też

- [Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
