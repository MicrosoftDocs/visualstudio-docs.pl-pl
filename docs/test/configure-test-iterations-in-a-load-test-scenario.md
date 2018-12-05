---
title: Konfigurowanie iteracji testowych dla testy obciążeniowe w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, sceanrios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: f5ec275c4b6e7fcf239aa0903ffe68757c5412cc
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896214"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurowanie iteracji testowych w scenariuszu testu obciążenia

Aby skonfigurować ustawienia iteracji testu, edytować Scenariusz testów obciążenia za pomocą edytora testu obciążenia i **właściwości** okna. Domyślnie scenariusza testu obciążeniowego jest skonfigurowany bez określania opcji Maksymalna liczba iteracji testu. Masz możliwość skonfigurowania maksymalną liczbę iteracji, w tym scenariuszu i długość przerwy między nimi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Określ maksymalna liczba iteracji testu dla scenariusza

Można określić maksymalną liczbę razy, które mają testów do uruchamiania dla scenariusza za pomocą edytora testu obciążenia, aby zmienić **maksymalna liczba iteracji testu** właściwość **właściwości** okna.

**Maksymalna liczba iteracji testu** właściwość kontroluje maksymalną liczbę iteracji testu do uruchomienia dla tego scenariusza. Podobnie jak w przypadku **iteracje testu** parametrów uruchomieniowych właściwości w teście obciążenia, nie jest to maksymalna dla wszystkich użytkowników dla wszystkich agentów według ustawień użytkownika.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

 W przypadku sekwencyjnych testu mieszanego jednej iteracji jest jeden przekazuj wszystkie testy w asortymencie. Dla wszystkich innych mieszanki testów każdego wykonania testu jest liczona jako iteracji. Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

 Jeśli test obciążenia jest test obciążenia opartego na czasie trwania i wygaśnięciu czasu trwania przed zakończeniem liczbę iteracji, test nadal zostanie zatrzymane. Jeśli test jest oparte na iteracji i iteracjami testu są spełnione przed iteracji w scenariuszu, test zostanie zatrzymane. Czas trwania jest konfigurowana przy użyciu **czas trwania uruchomienia** właściwość **właściwości** okna skojarzonych ustawieniach testu w teście obciążeniowym.

 Po spełnieniu scenariusz liczby iteracji scenariusza przestanie działać, ale inne scenariusze active będą nadal działać.

> [!NOTE]
> Powiązane właściwości **unikatowe** właściwości w źródle danych testu sieci web, która przenosi sekwencyjnie przez dane, wiersz po wierszu, ale tylko jeden raz dla każdego rekordu. Aby uzyskać więcej informacji, zobacz [Dodawanie źródła danych do testu wydajności sieci web](../test/add-a-data-source-to-a-web-performance-test.md).

 **Maksymalna liczba iteracji testu** właściwość jest przydatna dla wielu różnych sytuacjach. Testerzy obciążenia wolą należy przeprowadzić testowanie oparte na iteracji, natomiast inne obciążenia testerów Preferuj przeprowadzenie testowania opartego na czasie trwania.

 ![Określanie iteracji testowych w scenariuszu](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Aby określić, maksymalna liczba iteracji testu

1. Otwórz test obciążenia.

2. Zostanie wyświetlony Edytor testów obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

3. Obciążenia test drzew **scenariuszy** folderu, wybierz węzeł scenariusz, dla którego chcesz określić maksymalną liczbę iteracji testu.

4. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w **właściwości** okna.

5. W polu tekstowym dla **maksymalna liczba iteracji testu** właściwości, wpisz wartość, która określa maksymalną liczbę testów do uruchomienia w ramach scenariusza opisywanego po uruchomieniu testu obciążenia.

    > [!NOTE]
    > Przy użyciu wartości 0 dla **maksymalna liczba iteracji testu** właściwość określa nie maksymalna liczba iteracji.

6. Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić testu obciążenia za pomocą nowego **maksymalna liczba iteracji testu** wartość.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Określić czasy reakcji pomiędzy iteracjami testu dla scenariusza

**Traktować czas między iteracjami testu** właściwość można ustawić przy użyciu **właściwości** okna podczas edytowania właściwości scenariusza testów obciążenia w edytorze testu obciążeniowego.

**Traktować czas między iteracjami testu** właściwość jest używana, aby określić liczbę sekund oczekiwania przed rozpoczęciem iteracji testu.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Aby określić czas namysłu pomiędzy iteracjami testu

1. Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariuszy** folderu, wybierz węzeł scenariusz, aby określić czas namysłu na potrzeby.

3. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w **właściwości** okna.

4. Wartości **traktować czas między iteracjami testu** właściwość, wprowadź liczbę reprezentującą liczbę sekund oczekiwania przed rozpoczęciem następnej iteracji testu.

5. Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie możesz uruchomić test obciążenia za pomocą nowego **traktować czas między iteracjami testu** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i kontrolerów testów obciążenia testów](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Edytowanie czasów reakcji w celu symulowania witryny sieci Web symulujący opóźnienia wynikające z](../test/edit-think-times-in-load-test-scenarios.md)