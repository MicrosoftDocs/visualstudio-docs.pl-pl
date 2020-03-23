---
title: Konfigurowanie iteracji testowych do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e95ca27ace50c7b28d1ffb1d3fc02589daddee2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590985"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurowanie iteracji testowych w scenariuszu testu obciążenia

Aby skonfigurować ustawienia iteracji testowej, edytuj scenariusz testu obciążenia przy użyciu Edytora testów obciążenia i okna **Właściwości.** Domyślnie scenariusz testu obciążenia jest skonfigurowany bez określania maksymalnych iteracji testowych. Istnieje możliwość skonfigurowania maksymalnej liczby iteracji w scenariuszu i jak długo, aby wstrzymać między nimi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Określanie maksymalnych iteracji testowych dla scenariusza

Można określić maksymalną liczbę razy, które mają być uruchamiane dla scenariusza za pomocą Edytora testów obciążenia, aby zmienić **maksymalną iteracje testu** właściwości w oknie **Właściwości.**

**Właściwość Maksymalna iteracje testu** kontroluje maksymalną liczbę iteracji testowych do uruchomienia dla scenariusza. Podobnie jak w przypadku **test iteracji** właściwości w ustawieniach przebiegu testu obciążenia jest to maksymalna wartość wszystkich użytkowników na wszystkich agentów, a nie ustawienie na użytkownika.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia.](../test/load-test-scenario-properties.md)

Dla sekwencyjnego testu mix, jedna iteracja jest jeden przejść przez wszystkie testy w mieszance. Dla wszystkich innych mieszanek testowych każde wykonanie testu liczy się jako iteracji. Aby uzyskać więcej informacji, zobacz [Informacje o formancie mieszania](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Jeśli test obciążenia jest test obciążenia na podstawie czasu trwania, a czas trwania wygasa przed zakończeniem liczby iteracji, test będzie nadal zatrzymać. Jeśli test jest oparty na iteracji, a iteracje testowe są spełnione przed iteracji scenariusza, test zostanie zatrzymany. Czas trwania jest konfigurowany przy użyciu **Run Duration** właściwość w **właściwości okna skojarzone** z ustawieniem uruchomienia w teście obciążenia.

Po spełnieniu licznika iteracji scenariusza scenariusz przestanie działać, ale wszystkie inne aktywne scenariusze będą nadal działać.

> [!NOTE]
> Właściwość pokrewna jest **Właściwość Unique** w źródle danych testu sieci web, która przenosi się sekwencyjnie przez dane, wiersz po wierszu, ale tylko jeden raz dla każdego rekordu. Aby uzyskać więcej informacji, zobacz [Dodawanie źródła danych do testu wydajności sieci Web](../test/add-a-data-source-to-a-web-performance-test.md).

**Właściwość Maksymalna iteracje testu** jest przydatna w różnych sytuacjach. Niektóre testery obciążenia wolą przeprowadzać testy oparte na iteracji, podczas gdy inni testerzy obciążenia wolą przeprowadzać testy oparte na czasie trwania.

![Określanie iteracji testowych w scenariuszu](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Aby określić maksymalną iteracji testowych

1. Otwórz test obciążenia.

2. Pojawi się Edytor testów obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

3. W folderze **Scenariusze** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić maksymalną liczbę iteracji testowych.

4. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

5. W polu tekstowym właściwości **Maksymalna iteracja testu** wpisz wartość, która wskazuje maksymalną liczbę testów do uruchomienia dla scenariusza po uruchomieniu testu obciążenia.

    > [!NOTE]
    > Przy użyciu wartości 0 dla **właściwości Maksymalna iteracja testu** określa żadnych maksymalnych iteracji.

6. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **maksymalnej iteracji testu.**

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Określanie czasów oddawania myśli między iteracjami testu dla scenariusza

**Właściwość Think Time Between Test Iterations** jest ustawiana przy użyciu okna **Właściwości** podczas edytowania właściwości scenariusza testu obciążenia w Edytorze testów obciążenia.

**Właściwość Think Time Between Test Iterations** służy do określania ilości sekund oczekiwania przed rozpoczęciem iteracji testu.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Aby określić czas namysł między iteracjami testu

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **Scenariusze** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić czas na myślenie.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości.**

4. W wartości **think time between test iteracji** właściwości wprowadź liczbę reprezentującą liczbę sekund oczekiwania przed rozpoczęciem następnej iteracji testu.

5. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **think time między iteracjami testu.**

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i kontrolerów testów do testów obciążenia](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
- [Edytuj czasy zajmów się, aby symulować opóźnienia interakcji z człowiekiem w witrynie](../test/edit-think-times-in-load-test-scenarios.md)
