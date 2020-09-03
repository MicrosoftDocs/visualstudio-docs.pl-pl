---
title: Konfigurowanie iteracji testowych na potrzeby testowania obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6adbdedf8a71319877c5527e00e0e7c5e73fa6b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288783"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurowanie iteracji testowych w scenariuszu testu obciążenia

Aby skonfigurować ustawienia iteracji testu, Edytuj scenariusz testu obciążenia przy użyciu Edytor testu obciążeniowego i okna **Właściwości** . Domyślnie scenariusz testu obciążenia jest ustawiany bez określenia maksymalnej iteracji testu. Można skonfigurować maksymalną liczbę iteracji w scenariuszu i czas ich wstrzymywania między nimi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Określ maksymalną liczbę iteracji testu dla scenariusza

Można określić maksymalną liczbę prób uruchomienia testów dla scenariusza przy użyciu Edytor testu obciążeniowego, aby zmienić właściwość **maksymalnej liczby iteracji testu** w oknie **Właściwości** .

Właściwość **Maksymalna liczba iteracji testu** kontroluje maksymalną liczbę iteracji testowych do uruchomienia dla scenariusza. Tak jak w przypadku właściwości **iteracje testu** w ustawieniach przebiegu testu obciążenia, jest to wartość maksymalna dla wszystkich użytkowników na wszystkich agentach, a nie dla poszczególnych ustawień użytkownika.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

Dla sekwencyjnych testów mieszanych Jedna iteracja to jeden przebieg przez wszystkie testy w mieszaninie. Dla wszystkich innych miksów testowych każde wykonanie testu jest liczone jako iteracja. Aby uzyskać więcej informacji, zobacz [Informacje o kontrolce mieszanej](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Jeśli test obciążenia jest testem obciążenia opartym na czasie trwania, a czas trwania upływa przed ukończeniem iteracji, test nadal zostanie zatrzymany. Jeśli test jest oparty na iteracji, a iteracje testu są spełnione przed iteracjami scenariuszy, test zostanie zatrzymany. Czas trwania jest konfigurowany przy użyciu właściwości **Run Duration** w oknie **Właściwości** skojarzonym z ustawieniem Run w teście obciążenia.

Gdy liczba iteracji scenariusza zostanie osiągnięta, scenariusz przestanie działać, ale wszystkie inne aktywne scenariusze będą nadal działać.

> [!NOTE]
> Właściwość powiązana jest **unikatową** właściwością w źródle danych testu sieci Web, która przenosi się sekwencyjnie przez dane, wiersz po wierszu, ale tylko jeden raz dla każdego rekordu. Aby uzyskać więcej informacji, zobacz [Dodawanie źródła danych do testu wydajności sieci Web](../test/add-a-data-source-to-a-web-performance-test.md).

Właściwość **maksymalnej liczby iteracji testu** jest przydatna w różnych sytuacjach. Niektórzy testerzy obciążenia wolą przeprowadzić testy oparte na iteracji, natomiast inni testerzy obciążenia wolą przeprowadzić testy oparte na czasie trwania.

![Określanie iteracji testowych w scenariuszu](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Aby określić maksymalną liczbę iteracji testu

1. Otwórz test obciążenia.

2. Zostanie wyświetlona Edytor testu obciążeniowego. Zostanie wyświetlone drzewo testu obciążenia.

3. W folderze **scenariusze** dla drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić maksymalną liczbę iteracji testowych.

4. W menu **Widok** wybierz polecenie **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości** .

5. W polu tekstowym dla właściwości **Maksymalna liczba iteracji testu** wpisz wartość wskazującą maksymalną liczbę testów do uruchomienia dla scenariusza, gdy test obciążenia jest uruchomiony.

    > [!NOTE]
    > Użycie wartości 0 dla właściwości maksymalna liczba **iteracji testu** określa brak maksymalnych iteracji.

6. Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie można uruchomić test obciążenia przy użyciu nowych wartości **iteracji testu maksymalnego** .

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Określ czasy reakcji między iteracjami testu dla scenariusza

Właściwość **czas reakcji między iteracjami testu** jest ustawiana za pomocą okna **Właściwości** podczas edytowania właściwości scenariusza testu obciążenia w Edytor testu obciążeniowego.

Właściwość **czas reakcji między iteracjami testu** służy do określania liczby sekund oczekiwania przed rozpoczęciem iteracji testu.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Aby określić czas reakcji między iteracjami testu

1. Otwórz test obciążenia.

     Zostanie wyświetlona **Edytor testu obciążeniowego** . Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **scenariuszy** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić czas reakcji.

3. W menu **Widok** wybierz polecenie **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w oknie **Właściwości** .

4. W polu wartość **czasu reakcji między iteracjami testu** wprowadź liczbę określającą liczbę sekund oczekiwania przed rozpoczęciem następnej iteracji testu.

5. Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie można uruchomić test obciążenia przy użyciu nowego **czasu reakcji między wartością iteracji testu** .

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i kontrolerów testów dla testów obciążenia](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie czasów reakcji w celu symulowania opóźnień interakcji z witryną sieci Web](../test/edit-think-times-in-load-test-scenarios.md)
