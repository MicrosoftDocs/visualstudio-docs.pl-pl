---
title: Tworzenie wizualizacji kodu
description: Dowiedz się, jak używać narzędzi do wizualizacji i modelowania w Visual Studio, aby zrozumieć istniejący kod i opisać aplikację.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90c180bf9d910227013c2e089001ce5332cd1bd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388350"
---
# <a name="visualize-code"></a>Tworzenie wizualizacji kodu

Możesz użyć narzędzi do wizualizacji i modelowania w Visual Studio, aby ułatwić zrozumienie istniejącego kodu i opisanie aplikacji. Dzięki temu można wizualnie dowiedzieć się, jak zmiany mogą wpłynąć na kod, oraz ułatwić ocenę pracy i ryzyka wynikającego z tych zmian. Na przykład:

- Aby zrozumieć relacje w kodzie, zamapuj je wizualnie.

- Aby opisać architekturę systemu i zachować spójność kodu z jego projektem, utwórz diagramy zależności i zweryfikuj kod względem tych diagramów.

- Aby opisać struktury klas, utwórz diagramy klas.

Te narzędzia ułatwiają również komunikowanie się z osobami zaangażowanymi w projekt.

Aby sprawdzić, które wersje Visual Studio obsługują każdą funkcję, zobacz Obsługa wersji dla [architektury i narzędzi do modelowania](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|Scenariusz|Artykuły|
|-|-|
|**Opis kodu i jego relacji:**<br /><br /> Mapowanie relacji między określonymi fragmentami kodu.<br /><br /> Zapoznaj się z omówieniem relacji w kodzie dla całego rozwiązania.|- [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Debugowanie aplikacji przy użyciu map kodu](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Znajdowanie potencjalnych problemów przy użyciu analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Opis struktur klas:**<br /><br /> Wizualizowanie struktury klas w projekcie przez utworzenie diagramów klas z kodu.|[Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Opisz projekt systemu wysokiego poziomu i zweryfikuj kod względem tego projektu:**<br /><br /> Opisz projekt systemu wysokiego poziomu i jego zamierzone zależności, tworząc diagramy zależności. Zweryfikuj kod względem tego projektu, aby upewnić się, że zależności w kodzie pozostają zgodne z projektem.|- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Weryfikowanie kodu za pomocą diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Zobacz też

- [Instalowanie narzędzi kodu architektury](install-architecture-tools.md)
- [Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
