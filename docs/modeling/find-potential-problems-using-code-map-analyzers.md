---
title: Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 04e4d51fba62c56ce39fd34d8179f73baeeea77a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025920"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu

Uruchomić analizatory na mapach kodu, aby ułatwić identyfikację kodu, który może być zbyt skomplikowana, lub który może być konieczne poprawy jakości obsługi. Na przykład można użyć tych analizatory:

|**Aby znaleźć kod, który posiada**|**Sprawdź tych obszarów, aby zobaczyć, czy**|
|-|-|
|Pętle lub zależności cykliczne|Możesz uprościć i należy wziąć pod uwagę, czy możesz przerwać tych cykli.|
|Zbyt wiele zależności|Działają one zbyt wiele funkcji lub określić wpływ zmiany na tych obszarów. Mapy kodu z dobrze sformułowany pokaże minimalnej liczby zależności. Aby ułatwić kod obsługi, zmienianie, przetestować i ponownie użyć, należy rozważyć, czy Refaktoryzacja tych obszarów, aby wyraźniej zdefiniowano lub tego, czy można scalać kod, który wykonuje podobne funkcje.|
|Brak zależności|Jest to konieczne, lub czy należy usunąć ten kod.|

## <a name="analyze-code-maps"></a>Analizowanie mapy kodu

Na pasku narzędzi mapy wybierz **układ** > **analizatory**, a następnie analizatora, które chcesz uruchomić:

|**Analyzer**|**Do identyfikowania węzłów,**|
|-|-|
|**Analizator odwołań cyklicznych**|Mają zależności cykliczne na siebie nawzajem. **Uwaga:**  Zależności cykliczne, które znajdują się w **ogólne** grupy nie są wyświetlane na mapie, po rozwinięciu grupy.|
|**Znajdź analizator koncentratory**|Znajdują się w 25% najlepszych wysoce połączone węzły<br /><br /> **Aby ukryć wszystkie węzły na mapie**<br /><br /> -Otwórz menu skrótów dla mapy, wybierz **zaawansowane**, **wybierz**, **Ukryj niezaznaczone**.<br />     Mapa ukrywa węzły niezaznaczone i analizatora identyfikuje nowe węzły rolę piast.|
|**Analizator węzłów bez odwołań**|Nie ma odwołań z innych węzłów. **Uwaga:**  Sprawdź każdy z tych przypadków przed, przy założeniu, że kod nie jest używany. Niektóre zależności, np. zależności XAML i środowiska wykonawczego zależności nie można odnaleźć statycznie w kodzie.|

Analizatorów mapy kodu będzie kontynuowane po ich zastosowania. W przypadku zmiany mapy analizatorów zastosowany zostanie automatycznie ponownie przetworzyć zaktualizowano mapę. Aby zatrzymać analizatora, na pasku narzędzi mapy, wybierz opcję **układ** > **analizatory**. Wyłącz wybrane analizatora.

> [!TIP]
> W przypadku bardzo dużych mapy uruchomiony analizator może spowodować wyjątek braku pamięci. Jeśli ten problem wystąpi, Edytuj mapę, aby zmniejszyć jego zakres lub wygenerować mniejszych, a następnie uruchom analizator.

## <a name="see-also"></a>Zobacz także

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
