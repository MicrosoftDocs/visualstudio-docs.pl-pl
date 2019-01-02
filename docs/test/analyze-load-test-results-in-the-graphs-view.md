---
title: Analizowanie wyników testów obciążenia w widoku wykresu analizatora testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: f27689d5e3c322a539a0db5ee1f93c569cb181a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914560"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia w widoku wykresu analizatora testu obciążenia

Wyniki testu obciążeniowego są wyświetlane jako dane w kilku różnych okienek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby wyświetlić wyniki testów jako wykresy, wybierz opcję **wykresów** na **testu obciążeniowego** paska narzędzi. Każdy Graf poszczególnych są wyświetlane w panelu nazwy programu graph, wyświetlane u góry na liście rozwijanej. Aby wyświetlić inny wykres na panelu, wybierz nazwę innego wykresu z listy.

Maksymalnie cztery wykres panele mogą być wyświetlane w danym momencie. Możesz przełączać się między różnych paneli układów przy użyciu **Układ panelu** przycisku paska narzędzi.

Kilka wbudowanych wykresy. Można użyć wbudowanego wykresów, ponieważ jest lub dostosować je. Ponadto można utworzyć własnego wykresów. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) i [jak: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Wbudowane wykresów

Poniższa tabela zawiera listę wbudowanych wykresów, które są dostępne do analizowania wyników testów obciążenia.

|Nazwa wykresu|Opis|
|-|-|
|Kluczowe wskaźniki|Liczniki, które opisują podstawowych aspektów testowanie wydajności, takie jak czas ładowania, przepływność i odpowiedzi użytkownika.|
|Czas odpowiedzi testu|Dane dotyczące ilości czasu testy wykonać, aby uruchomić.|
|Czas odpowiedzi strony|Średni czas odpowiedzi dla stron sieci web, które są dostępne podczas testu obciążeniowego.|
|System w trakcie testu|Informacje o komputerach, na których aplikacja testowana przebiegów. Obejmuje to dane dotyczące użycia pamięci, procesora, dysku fizycznego, procesów.<br /><br /> Domyślnie są zbierane tylko liczniki dostępna pamięć (MB) i czasu procesora.|
|Kontroler i agentów|Informacje o komputerach, na których Uruchom testy obciążenia. Obejmuje to dane dotyczące użycia pamięci, procesora, dysku fizycznego, procesów.<br /><br /> Domyślnie tylko dostępnej ilości megabajtów i są zbierane przez liczniki czas procesora.|
|Czas odpowiedzi transakcji|Średni czas odpowiedzi transakcji, które występują podczas testu obciążeniowego.|

 Możesz wyświetlić różne liczniki na wykresie, w czasie wykonywania i po wykonaniu testu.

> [!NOTE]
> Tylko liczniki wydajności czasu odpowiedzi można dodać do wykresu czasu odpowiedzi automatycznie wygenerowany.

 Informacje o liczniku wyświetla zarówno na wykresie, a w legendzie poniżej wykresy. Możesz również powiększać sekcji wykresu. Aby uzyskać więcej informacji, zobacz [jak: Powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Liczniki wyświetlane na wykresach

 Wyświetlanie wykresów *liczniki*. Liczniki dotyczą danych zebranych podczas testu obciążenia, takich jak testy na sekundę lub średnia test czasu. Aby uzyskać więcej informacji na temat liczników, zobacz [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

 Legenda liczniki, które są wyświetlane na wykresach zawiera kilka kolumn użyteczne dane na temat przebiegu testu obciążeniowego. Aby wyłączyć funkcję wyświetlania wszystkich danych na wykresie, wyczyść pole wyboru w wierszu w legendzie.

 Legenda zawiera następujące kolumny:

|Licznik|Nazwa licznika|
|-|-|
|Wystąpienie|Nazwa wystąpienia licznika.|
|Kategoria|Nazwa kategorii licznika.|
|Komputer|Nazwa komputera, do którego zbierane są licznika.|
|Kolor|Kolor linii na wykresie.|
|Zakres|Określa liczbę, która jest reprezentowana przez 100 na wykresie dla tego licznika. Na przykład dla zakresu, w której górna wartość wynosi 10 000, 100 etykiety w górnej części wykresu reprezentuje 10 000.|
|Min.|Wskazuje wartość minimalna dla licznika (w milisekundach).|
|Maks.|Wskazuje maksymalną wartość licznika w milisekundach.|
|Średni|Wskazuje, średnia wartość licznika w milisekundach.|
|Ostatnia|Przedstawia wartość licznika w interwale próbkowania najbardziej aktualne w milisekundach.|

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Dostosowywanie wykresów za pomocą legendy:** Wykresy wyświetlić legendy Wyświetla informacje dla każdego licznika wydajności, który jest skojarzony z wykresu. Aby usunąć liczniki wydajności, wyróżnij liczników wydajności na wykresie i Dostosuj opcje wykreślania, można użyć legendy.|-   [Korzystanie z legendy wykresu do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Wyświetl liczników na wykresach:** Możesz dodać różne rodzaje danych na wykres wyników testu obciążenia, umieszczając liczniki na wykresie.|-   [Jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Powiększanie wykresy:** Po zakończeniu testu obciążeniowego umożliwia powiększenie paski powiększyć obraz i przewiń do obszaru wykresu. Przez powiększyć, można sprawdzić dane, który został wygenerowany podczas testu obciążenia uruchamiane w bardziej szczegółowo.|-   [Jak: Powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Kafelkowe:** Można rozmieścić wykresy wyników testu obciążenia w jednym z kilku wzorców. Można kafelka maksymalnie cztery wykresy.||
|**Tworzenie wykresów niestandardowych:** Można zaprojektować wykresów wyświetlających określone informacje na temat wyników testów obciążenia. Projektujesz niestandardowy wykres, określając liczniki testu obciążenia, które wykresie będą wyświetlane.|-   [Jak: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Eksportuj dane liczników wydajności na wykresie:** Możesz wyeksportować dane wykresu do programu Microsoft Excel za pomocą **Eksportuj dane wykresu do programu Excel** znajdujący się na **analizatora testu obciążenia** narzędzi, gdy jesteś w **wykresów** widoku.||

## <a name="related-tasks"></a>Zadania powiązane

 [Analizowanie wyników testów obciążenia oraz błędów w widoku tabeli](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

 [Instrukcje: Wyniki testu obciążeniowego dostęp do analizy](../test/how-to-access-load-test-results-for-analysis.md)

 [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Instrukcje: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Instrukcje: Powiększanie obszaru wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)