---
title: Wizualizuj kod | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ffd105032cda050ab16132b6a4c2d54488028b8
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586769"
---
# <a name="visualize-code"></a>Tworzenie wizualizacji kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia do wizualizacji i modelowania w programie Visual Studio ułatwiają zapoznanie się z istniejącym kodem i opisywanie aplikacji. Dzięki temu można wizualnie dowiedzieć się, jak zmiany mogą wpływać na kod i pomóc w ocenie pracy i zagrożeń wynikających z tych zmian. Przykład:

- Aby zrozumieć relacje w kodzie, zamapuj je wizualnie.

- Aby opisać architekturę systemu i zachować spójność kodu z projektem, Utwórz diagramy warstwowe i sprawdź poprawność kodu względem tych diagramów.

- Aby opisać struktury klas, Utwórz diagramy klas.

- Aby modelować i komunikować różne aspekty systemu, Rysuj diagramy UML (UML). Na przykład można modelować składniki systemu, typy, interakcje i procesy.

  Te narzędzia ułatwiają również szybkie komunikowanie się z osobami korzystającymi z Twojego projektu. Na przykład można użyć diagramów klas UML do utworzenia wspólnego słownika do omówienia systemu przy użyciu uczestników projektu, użytkowników i członków zespołu.

  Aby sprawdzić, które wersje programu Visual Studio obsługują każdą funkcję, zobacz [Obsługa wersji dla narzędzi architektura i modelowanie](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|||
|-|-|
|**Opis kodu i jego relacji:**<br /><br /> Mapuj relacje między określonymi fragmentami kodu.<br /><br /> Zapoznaj się z omówieniem relacji w kodzie dla całego rozwiązania.<br /><br /> **Uwaga**: w tej wersji programu Visual Studio termin *Mapa kodu* jest używana zamiast *grafu zależności*.|-   [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Znajdowanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Mapuj metody na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Opis struktur klas:**<br /><br /> Wizualizuj strukturę klas w projekcie, tworząc diagramy klas z kodu.|[Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Opisz projekt systemu wysokiego poziomu i sprawdź poprawność kodu dla tego projektu:**<br /><br /> Opisz projekt systemu wysokiego poziomu i jego zamierzone zależności, tworząc diagramy warstwowe. Sprawdź poprawność kodu względem tego projektu, aby upewnić się, że zależności w kodzie pozostają spójne z projektem.|-   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: Dokumentacja](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: wytyczne](../modeling/layer-diagrams-guidelines.md)<br />-   [Sprawdzanie poprawności kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|
|**Przekaż wymagania i architekturę użytkownika:**<br /><br /> Należy modelować wymagania i architekturę systemu oprogramowania przez rysowanie następujących diagramów UML: działania, składnika, klasy, sekwencji i przypadku użycia.|-   [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md)<br />-   [Wymagania dotyczące użytkownika modelu](../modeling/model-user-requirements.md)<br />-   [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|------------------|---------------|
|**Fora**|-   [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Wizualizacja & modelowania SDK (narzędzia DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogi**|[Blog programu Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Artykuły techniczne i dzienniki**|[Forum architektury MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Zobacz też
 [Scenariusz: zmiana projektu przy użyciu wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) modelowanie [i architektura](../modeling/analyze-and-model-your-architecture.md) modelowanie [Tworzenie modeli dla](../modeling/create-models-for-your-app.md) modelu [wymagań użytkowników](../modeling/model-user-requirements.md) modelu aplikacji [Używanie modeli w procesie tworzenia](../modeling/use-models-in-your-development-process.md) [aplikacji](../modeling/model-your-app-s-architecture.md)
