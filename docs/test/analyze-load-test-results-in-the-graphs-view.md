---
title: Analizowanie wyników testów obciążenia — widok wykresów (Analizator testu obciążenia)
description: Dowiedz się, jak wyświetlać wyniki testów jako wykresy. Każdy wykres jest wyświetlany w panelu z nazwą grafu na liście rozwijanej.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: cbd15d57090f2248cdd97eba1898e363cc2d21b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948078"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analizowanie wyników testów obciążenia w widoku wykresy analizatora testu obciążenia

Wyniki testu obciążenia są wyświetlane jako dane w kilku różnych okienkach.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby wyświetlić wyniki testów jako wykresy, wybierz **Wykres** na pasku narzędzi **testu obciążenia** . Każdy pojedynczy wykres jest wyświetlany w panelu z nazwą wykresu wyświetlaną u góry na liście rozwijanej. Aby wyświetlić inny wykres w panelu, wybierz inną nazwę wykresu z listy.

Można wyświetlać maksymalnie cztery panele grafu. Można przełączać się między różnymi układami panelu przy użyciu przycisku paska narzędzi **układu panelu** .

Dostępne są kilka wbudowanych grafów. Możesz użyć wbudowanych grafów jako programu lub można je dostosować. Ponadto można tworzyć własne wykresy. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) i [instrukcje: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Wykresy wbudowane

W poniższej tabeli przedstawiono wbudowane wykresy, które są dostępne do analizowania wyników testów obciążenia.

|Nazwa wykresu|Opis|
|-|-|
|Kluczowe wskaźniki|Liczniki opisujące podstawowe aspekty wydajności testów, takie jak obciążenie użytkownikami, przepływność i czas odpowiedzi.|
|Czas odpowiedzi testu|Dane dotyczące ilości testów czasowych, które należy wykonać.|
|Czas odpowiedzi strony|Średni czas odpowiedzi dla stron sieci Web, do których uzyskuje się dostęp w trakcie testu obciążenia.|
|System w trakcie testu|Informacje o komputerach, na których są uruchamiane testowane aplikacje. Obejmuje to dane dotyczące użycia pamięci, procesora, dysku fizycznego i procesów.<br /><br /> Domyślnie zbierane są tylko liczniki dostępne (MB i czas procesora).|
|Kontroler i agenci|Informacje o komputerach, na których uruchomiono testy obciążenia. Obejmuje to dane dotyczące użycia pamięci, procesora, dysku fizycznego i procesów.<br /><br /> Domyślnie są zbierane tylko dostępne liczniki (MB i czas procesora).|
|Czas odpowiedzi transakcji|Średni czas odpowiedzi dla transakcji, które wystąpiły w trakcie testu obciążenia.|

Można wyświetlić różne liczniki na wykresie zarówno w czasie wykonywania, jak i po uruchomieniu testu.

> [!NOTE]
> Tylko liczniki wydajności czasu odpowiedzi mogą zostać dodane do generowanego automatycznie wykresu czasu odpowiedzi.

Informacje o licznikach są wyświetlane zarówno na grafie, jak i w legendzie poniżej wykresów. Możesz również powiększać w sekcji grafu. Aby uzyskać więcej informacji, zobacz [jak: powiększanie w regionie grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Liczniki wyświetlane na wykresach

Wykresy przedstawiające *liczniki*. Liczniki odnoszą się do danych zebranych podczas testu obciążenia, takich jak testy na sekundę lub średni czas testu. Aby uzyskać więcej informacji o licznikach, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

Legenda liczników, które są wyświetlane na wykresach, pokazuje kilka kolumn użytecznych danych dotyczących przebiegu testu obciążenia. Aby wyłączyć wyświetlanie danych na wykresie, wyczyść pole wyboru w wierszu legendy.

Legenda zawiera następujące kolumny:

|Licznik|Nazwa licznika|
|-|-|
|Wystąpienie|Nazwa wystąpienia licznika.|
|Kategoria|Nazwa kategorii licznika.|
|Computer (Komputer)|Nazwa komputera, do którego zostanie zebrany licznik.|
|Kolor|Kolor linii w grafie.|
|Zakres|Wskazuje liczbę, która jest reprezentowana przez 100 na wykresie dla tego licznika. Na przykład dla zakresu, którego górną wartością jest 10 000, etykieta 100 w górnej części wykresu reprezentuje 10 000.|
|Min|Określa minimalną wartość licznika w milisekundach.|
|Maks.|Wskazuje maksymalną wartość licznika w milisekundach.|
|Śr.|Wskazuje średnią wartość licznika w milisekundach.|
|Ostatnie|Pokazuje wartość licznika podczas ostatniego interwału próbkowania w milisekundach.|

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Dostosuj wykresy przy użyciu legendy:** Legenda widok wykresów wyświetla informacje dla każdego licznika wydajności, który jest skojarzony z wykresem. Możesz użyć legendy do usuwania liczników wydajności, wyróżniania liczników wydajności na grafie i dostosowania opcji wykreślania.|-   [Korzystanie z legendy widoku wykresy do analizowania testów obciążenia](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Wyświetl liczniki na wykresach:** Możesz dodać różne rodzaje danych do wykresu wyników testu obciążenia, umieszczając liczniki na wykresie.|-   [Instrukcje: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Powiększ wykresy:** Po zakończeniu testu obciążenia można użyć pasków powiększenia, aby powiększyć i przewinąć do regionu grafu. Powiększając, można sprawdzić dane, które zostały wygenerowane podczas przebiegu testu obciążenia, bardziej szczegółowo.|-   [Instrukcje: powiększanie w regionie wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Wykresy kafelkowe:** Wykresy wyników testów obciążenia można rozmieścić w jednym z kilku wzorców. Możesz podzielić na cztery wykresy.||
|**Utwórz wykresy niestandardowe:** Można zaprojektować wykresy, które wyświetlają określone informacje na temat wyników testu obciążenia. Wykres niestandardowy można zaprojektować, określając liczniki testów obciążenia, które będą wyświetlane na wykresie.|-   [Instrukcje: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Wyeksportuj dane liczników wydajności na grafie:** Możesz wyeksportować dane wykresu do programu Microsoft Excel, używając przycisku **Eksportuj dane wykresu do programu Excel** na pasku narzędzi **analizatora testu obciążenia** , gdy jesteś w widoku **wykresy** .||

## <a name="related-tasks"></a>Zadania powiązane

[Analizowanie wyników testów obciążenia i błędów w widoku tabel](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[Instrukcje: uzyskiwanie dostępu do wyników testu obciążenia na potrzeby analizy](../test/how-to-access-load-test-results-for-analysis.md)

[Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Dodawanie i usuwanie liczników na wykresach](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Instrukcje: Tworzenie wykresów niestandardowych](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Instrukcje: powiększanie w regionie wykresu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
