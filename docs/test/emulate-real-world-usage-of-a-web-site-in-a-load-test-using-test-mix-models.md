---
title: Emulacja rzeczywistego wykorzystania strony internetowej do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18e22cd151d8013a50e34a01757069dde9574e79
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589607"
---
# <a name="test-mix-models-overview"></a>Przegląd modeli miksu testowego

Opcje modelowania ładowania służą do dokładniejszego przewidywania oczekiwanego rzeczywistego użycia witryny sieci Web lub aplikacji, które są testowania obciążenia. Należy to zrobić, ponieważ test obciążenia, który nie jest oparty na dokładnym modelu obciążenia, może generować mylące wyniki.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Ulepszenia modelu miksu testowego

Za pomocą Edytora testów obciążenia lub kreatora modelu mix testu, można określić następujące typy testu wymieszać dla scenariusza testu obciążenia. Aby uzyskać więcej informacji, zobacz [Zmienianie modelu miksu testowego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Można określić jedną z następujących opcji modelu testu dla scenariusza testu obciążenia:

- **Na podstawie całkowitej liczby testów:** Określa, który test wydajności sieci web lub jednostki jest uruchamiany, gdy użytkownik wirtualny rozpoczyna iterację testową. Na końcu testu obciążenia liczba razy, że określone uruchomienie testu dopasowane przypisany rozkład testu. Użyj tego modelu mix testu, gdy opierasz mix testu na procentach transakcji w dzienniku IIS lub w danych produkcyjnych. Aby uzyskać więcej informacji, zobacz [Wartość procentowa na podstawie rozpoczętych testów](#BasedOnTestsStarted).

- **Na podstawie liczby użytkowników wirtualnych:** Określa procent użytkowników wirtualnych, którzy będą uruchamiać określoną wydajność sieci web lub test jednostkowy. W dowolnym momencie testu obciążenia liczba użytkowników, którzy są uruchomione określonego testu odpowiada przypisanej dystrybucji. Użyj tego modelu mix testu, gdy są oparte mix testu na procent użytkowników, którzy są uruchomione określonego testu. Aby uzyskać więcej informacji, zobacz [Wartość procentowa na podstawie użytkowników wirtualnych](#PercentageBasedonVirtualUsers).

- **Na podstawie tempa użytkownika:** W trakcie testu obciążenia każdy test wydajności sieci web lub test jednostkowy jest uruchamiany określoną liczbę razy na użytkowników na godzinę. Użyj tego modelu mix testu, jeśli chcesz, aby użytkownicy wirtualni uruchomić test w określonym tempie przez cały test obciążenia. Aby uzyskać więcej informacji, zobacz [tempo testu mix](#PacingTestMix).

    > [!TIP]
    > Kiedy wybierasz **procentową kombinację testów** i kiedy wybierzesz **wartość procentową na podstawie wirtualnych użytkowników?** Różnica między tymi dwoma wyborami jest ważne, gdy niektóre testy w zestawieniu testowym mają znacznie dłuższy czas trwania niż inne testy. W tej sytuacji prawdopodobnie należy wybrać **wartość procentową na podstawie wirtualnych użytkowników**. Ten wybór pomaga uniknąć przebiegu testowego, w którym prawdopodobieństwo wzrasta, że zbyt wielu użytkowników będzie działać testy długoterminowe. Jeśli jednak wszystkie testy mają podobny czas trwania, można bezpieczniej wybrać **procentową mieszankę testu**.

- **Na podstawie kolejności:** Każdy użytkownik wirtualny uruchamia wydajność sieci web lub testy jednostkowe w kolejności, w. Użytkownik wirtualny kontynuuje przechodzenie do pracy w tej kolejności podczas wykonywania testów w tej kolejności. Aby uzyskać więcej informacji, zobacz [Kolejność sekwencyjna](#SequentialOrder).

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a>Procent na podstawie rozpoczętych testów

Dla każdego testu w mieszance można określić wartość procentową, która określa, jak często test jest wybierany jako następny test do uruchomienia. Na przykład można przypisać następujące wartości procentowe do trzech testów:

- TestA (50%)

- TestB (35%)

- TestC (15%)

Jeśli używasz tego ustawienia, następny test do uruchomienia jest oparty na przypisanych wartościach procentowych. Można to zrobić bez uwzględnienia liczby użytkowników wirtualnych, którzy są obecnie uruchomione każdego testu.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a>Procent na podstawie użytkowników wirtualnych
Ten model testu mix określa procent użytkowników wirtualnych, którzy uruchomią określonego testu. Jeśli używasz tego modelu testu mix, następny test do uruchomienia opiera się nie tylko na przypisane wartości procentowe, ale także na procent użytkowników wirtualnych, którzy są obecnie uruchomione określonego testu. W dowolnym momencie testu obciążenia liczba użytkowników, którzy są uruchomione określonego testu odpowiada przypisanej dystrybucji tak ściśle, jak to możliwe.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a>Mieszanka testowa tempa

Jeśli określisz tempo testu mix, można ustawić szybkość wykonywania testu dla każdego użytkownika wirtualnego dla każdego testu w zestawieniu testu. Dla każdego testu ta stawka jest wyrażona jako testy uruchamiane na użytkownika wirtualnego na godzinę. Na przykład można przypisać następujące tempo testu mix do następujących testów:

- TestA: 4 testy na użytkownika na godzinę

- TestB: 2 testy na użytkownika na godzinę

- TestC: 0,125 testów na użytkownika na godzinę

Jeśli używasz modelu mix testu tempa, aparat środowiska uruchomieniowego testu obciążenia gwarantuje, że rzeczywista szybkość, z jaką testy są uruchamiane jest mniejsza lub równa określonej szybkości. Jeśli testy są trwać zbyt długo, aby przypisany numer został ukończony, zwracany jest błąd.

Think **Time Between Test Iteracji** ustawienie nie ma zastosowania, gdy używasz mix testu tempa.

#### <a name="apply-distribution-to-pacing-delay"></a>Stosowanie dystrybucji do opóźnienia tempa
Wartość zastosuj **dystrybucję do pacing delay** właściwości w scenariuszu testu obciążenia można ustawić na true lub false:

- **Prawda:** Scenariusz zastosuje typowe opóźnienia dystrybucji statystycznej określone przez wartość w **testach na godzinę** kolumny w oknie dialogowym **Edytuj miks testowy.** Aby uzyskać więcej informacji, zobacz [Edytowanie modeli miksu tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

   Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartość w oknie dialogowym Edytuj mix **testu** dla zestawu testów do 2 użytkowników na godzinę. Jeśli **zastosuj dystrybucję do pacing delay** właściwość jest ustawiona na **True,** typowy rozkład statystyczny jest stosowany do czasu oczekiwania między testami. Testy będą nadal uruchamiać 2 testy na godzinę, ale niekoniecznie będzie to 30 minut między nimi. Pierwszy test mógł zostać uruchomiony po 4 minutach, a drugi po 45 minutach.

- **False:** Testy będą uruchamiane w określonym tempie określonym dla wartości w **testach na godzinę** kolumny w oknie dialogowym **Edytuj miks testowy.** Aby uzyskać więcej informacji, zobacz [Edytowanie modeli miksu tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

   Załóżmy na przykład, że masz **testy na użytkownika na godzinę** wartość w oknie dialogowym Edytuj mix **testu** dla zestawu testów do 2 użytkowników na godzinę. Jeśli **Zastosuj dystrybucji do pacing delay** właściwość jest **ustawiona**na False , są w zasadzie daje nie ma swobody podczas uruchamiania testów. Test będzie uruchamiany co 30 minut. To sprawia, że należy wykonać 2 testy na godzinę.

  Aby uzyskać więcej informacji, zobacz [Jak: Stosowanie dystrybucji do opóźnienia tempa podczas korzystania z modelu miksowania testu tempa użytkownika](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="sequential-order"></a><a name="SequentialOrder"></a>Kolejności
Wybranie na podstawie kolejności testu sekwencyjnego kolejność opcji sprawia, że każdy użytkownik wirtualny uruchomić wszystkie testy w scenariuszu w kolejności, w kolejności, w zależności od testów zostały zdefiniowane.

## <a name="test-iterations-property"></a>Właściwość iteracji testowych
We właściwościach Uruchom ustawienia można określić wartość właściwości Test Iterations. Ta wartość jest liczbą iteracji testu do uruchomienia w teście obciążenia. Po uruchomieniu określonej liczby iteracji testowych nie zostanie uruchomiona żadna dodatkowa iteracje testowe pomimo ustawień któregokolwiek z profilów obciążenia. Po zakończeniu określonej liczby iteracji testowych kończy się test obciążenia. Aby uzyskać więcej informacji, zobacz [Jak: Określanie liczby iteracji testowych w ustawieniu uruchamiania](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Inicjowanie i przerywanie testów
Można wybrać testy do uruchomienia na początku i na końcu sesji testowania obciążenia każdego użytkownika wirtualnego. Aby uzyskać więcej informacji, zobacz [Edytowanie modeli miksu tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

- **Zainicjować test**. Ten test jest uruchamiany przez każdego użytkownika wirtualnego przed uruchomieniem dowolnego z testów w zestawieniu testowym.

- **Zakończ test**. Ten test jest uruchamiany po uruchomieniu wszystkich testów dla określonego użytkownika wirtualnego.

  Należy zwrócić uwagę na następujące informacje na temat testu inicjowania i testu zakończenia:

- Można określić czas trwania testu obciążenia według czasu, a nie według liczby iteracji. W takim przypadku po zakończeniu trwania przebiegu testu obciążenia, test zakończenia nie zostanie uruchomiony.

- Jeśli test inicjowania jest test jednostkowy lub test wydajności sieci web, stan TestContext lub WebTestContext, obiekt po zakończeniu testu inicjowania jest zapisywany. Następnie będzie używany jako kontekst początkowy dla iteracji testów w zestawieniu testowym.

- Nowi użytkownicy, zgodnie z definicją w właściwości scenariusza Procent nowych użytkowników, zawsze wykonać test inicjowania, jedną iterację testu z testu mix i testu zakończenia.

## <a name="see-also"></a>Zobacz też

- [Edytowanie modeli mieszania tekstu w celu określenia prawdopodobieństwa uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytuj kombinację testów, aby określić, które testy mają być uwzględniane w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
- [Zmienianie modelu miksu testowego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
