---
title: Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu
description: Dowiedz się, jak uruchamiać analizatory na mapach kodu, aby ułatwić identyfikowanie kodu, który może być zbyt skomplikowany lub może wymagać poprawy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8817e50ae96a27f6b3b76e28262390271c1fdf4c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388857"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu

Uruchamiaj analizatory na mapach kodu, aby ułatwić identyfikację kodu, który może być zbyt złożony lub może wymagać poprawy. Można na przykład użyć tych analizatorów:

|**Aby znaleźć kod, który ma**|**Zbadaj te obszary, aby sprawdzić, czy**|
|-|-|
|Pętle lub zależności cykliczne|Można je uprościć i rozważyć, czy można przerwać te cykle.|
|Zbyt wiele zależności|Pełnią one zbyt wiele funkcji lub określają wpływ zmiany tych obszarów. Dobrze uformowana mapa kodu będzie pokazywać minimalną liczbę zależności. Aby ułatwić konserwację, zmienianie, testowanie i ponowne używanie kodu, należy rozważyć, czy można refaktoryzować te obszary, aby były bardziej zdefiniowane, czy można scalić kod wykonujący podobne funkcje.|
|Brak zależności|Są one niezbędne lub czy należy usunąć ten kod.|

## <a name="analyze-code-maps"></a>Analizowanie map kodu

Na pasku narzędzi mapy wybierz pozycję  >  **Analizatory układu,** a następnie analizator, który chcesz uruchomić:

|**Analizator**|**Aby zidentyfikować węzły, które**|
|-|-|
|**Circular References Analyzer**|Mają od siebie zależności cykliczne. **Uwaga:**  Zależności cykliczne, które znajdują się w **grupie Typy** ogólne, nie są wyświetlane na mapie po rozwinięciu grupy.|
|**Find Hubs Analyzer**|Znajdują się w 25% węzłów o wysokim stopniu połączenia<br /><br /> **Aby ukryć wszystkie inne węzły na mapie**<br /><br /> - Otwórz menu skrótów dla mapy, wybierz pozycję **Zaawansowane,** **Wybierz,** **Ukryj Niezaznajętą.**<br />     Mapa ukrywa niewyznane węzły, a analizator identyfikuje nowe węzły jako koncentratory.|
|**Analizator nieużywanych węzłów**|Nie ma odwołań z innych węzłów. **Uwaga:**  Sprawdź każdy z tych przypadków przed założeniem, że kod nie jest używany. Niektóre zależności, takie jak zależności XAML i zależności czasu uruchamiania, nie można znaleźć statycznie w kodzie.|

Analizatory mapy kodu będą nadal działać po ich zastosowaniu. Jeśli zmienisz mapę, wszystkie zastosowane analizatory będą automatycznie ponownie przetwarzać zaktualizowaną mapę. Aby zatrzymać uruchamianie analizatora, na pasku narzędzi mapy wybierz pozycję  >  **Analizatory układu**. Wyłącz wybrany analizator.

> [!TIP]
> Jeśli masz bardzo dużą mapę, uruchomienie analizatora może spowodować wyjątek braku pamięci. W takim przypadku edytuj mapę, aby zmniejszyć jej zakres lub wygenerować mniejszy, a następnie uruchom analizator.

## <a name="see-also"></a>Zobacz też

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
