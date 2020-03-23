---
title: Analizowanie wyników testu obciążenia w widoku Wykresy analizatora testów obciążenia
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dac639b8513e8ef675c6246476791b9351241130
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591271"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analizowanie wyników testu obciążenia w widoku Wykresy analizatora testów obciążenia

Wyniki testu obciążenia są wyświetlane jako dane w kilku różnych okienkach.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby wyświetlić wyniki testów jako wykresy, wybierz **wykresy** na pasku narzędzi **testu obciążenia.** Każdy wykres jest wyświetlany w panelu z nazwą wykresu wyświetlaną u góry listy rozwijanej. Aby wyświetlić inny wykres w panelu, wybierz inną nazwę wykresu z listy.

Jednocześnie mogą być wyświetlane maksymalnie cztery panele wykresów. Między różnymi układami paneli można przełączać się za pomocą przycisku paska narzędzi **układu panelu.**

Dostępnych jest kilka wbudowanych wykresów. Można użyć wbudowanych wykresów, jak jest lub można je dostosować. Ponadto można tworzyć własne wykresy. Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) i [Jak: Tworzenie niestandardowych wykresów](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Wbudowane wykresy

W poniższej tabeli wymieniono wbudowane wykresy, które są dostępne do analizowania wyników testów obciążenia.

|Nazwa wykresu|Opis|
|-|-|
|Kluczowe wskaźniki|Liczniki, które opisują podstawowe aspekty wydajności testu, takie jak obciążenie użytkownika, przepływność i czas odpowiedzi.|
|Czas reakcji testu|Dane dotyczące czasu, jaką należy uruchomić testy.|
|Czas odpowiedzi strony|Średni czas odpowiedzi dla stron sieci web, które są dostępne podczas testu obciążenia.|
|System w fazie testów|Informacje o komputerach, na których działa testowana aplikacja. Obejmuje to dane dotyczące wykorzystania pamięci, procesora, dysku fizycznego, procesów.<br /><br /> Domyślnie zbierane są tylko liczniki Dostępne bajty i Czas procesora.|
|Kontroler i agenci|Informacje o komputerach, na których są uruchamiane testy obciążenia. Obejmuje to dane dotyczące wykorzystania pamięci, procesora, dysku fizycznego, procesów.<br /><br /> Domyślnie zbierane są tylko liczniki Dostępne bajty i Czas procesora.|
|Czas odpowiedzi transakcji|Średni czas odpowiedzi dla transakcji, które występują podczas testu obciążenia.|

Można wyświetlić różne liczniki na wykresie zarówno w czasie wykonywania, jak i po uruchomieniu testu.

> [!NOTE]
> Tylko liczniki wydajności czasu odpowiedzi można dodać do automatycznie wygenerowanego wykresu czasu odpowiedzi.

Informacje o liczniku są wyświetlane zarówno na wykresie, jak i w legendzie pod wykresami. Można również powiększyć sekcję wykresu. Aby uzyskać więcej informacji, zobacz [Jak: Powiększanie regionu wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Liczniki wyświetlane na wykresach

Wykresy wyświetlają *liczniki*. Liczniki odnoszą się do danych zebranych podczas testu obciążenia, takich jak testy na sekundę lub średni czas testowania. Aby uzyskać więcej informacji na temat liczników, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

Legenda liczników, które są wyświetlane na wykresach pokazuje kilka kolumn przydatnych danych o przebiegu testu obciążenia. Aby wyłączyć wyświetlanie jakichkolwiek danych na wykresie, wyczyść pole wyboru w wierszu legendy.

Legenda zawiera następujące kolumny:

|Licznik|Nazwa licznika|
|-|-|
|Wystąpienie|Nazwa wystąpienia licznika.|
|Kategoria|Nazwa kategorii licznika.|
|Computer (Komputer)|Nazwa komputera, na którym jest zbierany licznik.|
|Kolor|Kolor linii na wykresie.|
|Zakres|Wskazuje liczbę, która jest reprezentowana przez 100 na wykresie dla tego licznika. Na przykład dla zakresu, którego górna wartość wynosi 10 000, etykieta 100 u góry wykresu reprezentuje 10 000.|
|Min.|Wskazuje minimalną wartość licznika w milisekundach.|
|Maks.|Wskazuje maksymalną wartość licznika w milisekundach.|
|Średnia|Wskazuje średnią wartość licznika w milisekundach.|
|Last|Pokazuje wartość licznika podczas ostatniego interwału próbkowania w milisekundach.|

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Dostosuj wykresy przy użyciu legendy:** Legenda widoku Wykresy wyświetla informacje dla każdego licznika wydajności skojarzonego z wykresem. Za pomocą legendy można usunąć liczniki wydajności, wyróżnić liczniki wydajności na wykresie i dostosować opcje kreślenia.|-   [Używanie legendy widoku wykresy do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Wyświetlanie liczników na wykresach:** Można dodać różne rodzaje danych do wykresu wyników testu obciążenia, umieszczając liczniki na wykresie.|-   [Jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Powiększ wykresy:** Po zakończeniu testu obciążenia można użyć pasków powiększenia, aby powiększyć i przewinąć do regionu wykresu. Powiększając, można sprawdzić dane, które zostały wygenerowane podczas testu obciążenia uruchomić w dokładniejszych szczegółach.|-   [Jak: Powiększanie regionu wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Wykresy płytek:** Można rozmieścić wykresy wyników testów obciążenia w dowolnym z kilku wzorców. Można kafelki do czterech wykresów.||
|**Tworzenie niestandardowych wykresów:** Można projektować wykresy, które wyświetlają określone informacje o wynikach testu obciążenia. Zaprojektować wykres niestandardowy, określając liczniki testu obciążenia, które będzie wyświetlany wykres.|-   [Jak: Tworzenie niestandardowych wykresów](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Wyeksportuj dane liczników wydajności na wykresie:** Dane wykresu można wyeksportować do programu Microsoft Excel za pomocą przycisku **Eksportuj dane wykresu do programu Excel** na pasku narzędzi **Analizator testu obciążenia,** gdy znajdujesz się w widoku **Wykresy.**||

## <a name="related-tasks"></a>Zadania powiązane

[Analizowanie wyników testów obciążenia i błędów w widoku tabel](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[Jak: Dostęp do wyników testów obciążenia do analizy](../test/how-to-access-load-test-results-for-analysis.md)

[Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Zobacz też

- [Jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Jak: Tworzenie niestandardowych wykresów](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Jak: Powiększanie regionu wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
