---
title: Emuluj rzeczywiste użycie witryny sieci Web na potrzeby testowania obciążenia
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4dbbc5ec2ead98f9b20cb137f9e15237c13cf80
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810314"
---
# <a name="test-mix-models-overview"></a>Przegląd modeli testów mieszanych

Opcja Załaduj model umożliwia dokładniejsze przewidywalność rzeczywistego użycia witryny sieci Web lub aplikacji, które są testowane. Należy to zrobić, ponieważ test obciążenia, który nie jest oparty na precyzyjnym modelu obciążenia, może generować błędne wyniki.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Ulepszenia modelu testu mieszanego

Korzystając z Edytor testu obciążeniowego lub Kreatora testów modelu testowego, można określić następujące typy testów mieszanych dla scenariusza testu obciążenia. Aby uzyskać więcej informacji, zobacz [Zmiana modelu testu mieszanego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Możesz określić jedną z następujących opcji modelu testu mieszanego dla scenariusza testu obciążenia:

- **W oparciu o łączną liczbę testów:** Określa, który test wydajności sieci Web lub testy jednostkowe są uruchamiane, gdy użytkownik wirtualny rozpocznie iterację testową. Na koniec testu obciążenia, ile razy określony przebieg testu pasuje do przypisanego rozkładu testowego. Ten model testu mieszanego jest używany, gdy bazowasz test mieszany dla procentu transakcji w dzienniku IIS lub w danych produkcyjnych. Aby uzyskać więcej informacji, zobacz [procent w oparciu o uruchomione testy](#BasedOnTestsStarted).

- **Na podstawie liczby wirtualnych użytkowników:** Określa wartość procentową użytkowników wirtualnych, którzy będą uruchamiać określony test wydajności sieci Web lub testy jednostkowe. W każdym punkcie testu obciążenia liczba użytkowników, którzy uruchamiali określony test, odpowiada przypisanej dystrybucji. Użyj tego modelu testu mieszanego, gdy tworzysz test mieszany na procent użytkowników, którzy uruchamiają określony test. Aby uzyskać więcej informacji, zobacz [procent na podstawie użytkowników wirtualnych](#PercentageBasedonVirtualUsers).

- **Na podstawie tempa użytkownika:** W trakcie testu obciążenia każdy test wydajności sieci Web lub test jednostkowy jest uruchamiany określoną liczbę razy dla poszczególnych użytkowników na godzinę. Użyj tego modelu testu mieszanego, jeśli chcesz, aby użytkownicy wirtualną uruchamiali test w pewnym tempie w trakcie testu obciążenia. Aby uzyskać więcej informacji, zobacz [tempem test mix](#PacingTestMix).

    > [!TIP]
    > Kiedy wybierasz **procentowy test mieszany** i wybierasz **wartość procentową na podstawie użytkowników wirtualnych**? Różnica między tymi dwoma opcjami jest ważna, gdy niektóre testy w teście mieszanym mają znacznie dłuższy czas trwania niż inne testy. W takiej sytuacji należy prawdopodobnie wybrać **wartość procentową na podstawie użytkowników wirtualnych**. Wybór ten pozwala uniknąć przebiegu testowego, w którym prawdopodobieństwo zwiększy się, że zbyt wielu użytkowników będzie uruchamiać testy długotrwałe. Jeśli jednak wszystkie testy mają podobne czasy trwania, można bezpiecznie wybrać **Procent testu mieszanego**.

- **W oparciu o kolejność sekwencyjną:** Każdy użytkownik wirtualny uruchamia testy wydajności sieci Web lub testów jednostkowych w kolejności, w której testy są zdefiniowane w scenariuszu. Użytkownik wirtualny kontynuuje przechodzenie przez testy w tej kolejności do momentu zakończenia testu obciążenia. Aby uzyskać więcej informacji, zobacz [kolejność sekwencyjna](#SequentialOrder).

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a> Procent w oparciu o uruchomione testy

Dla każdego testu w połączeniu można określić wartość procentową, która określa, jak często test jest wybierany jako następny test do uruchomienia. Na przykład można przypisać następujące wartości procentowe do trzech testów:

- A (50%)

- TestB (35%)

- TestC (15%)

Jeśli używasz tego ustawienia, następnym testem do uruchomienia jest na podstawie przypisanych wartości procentowych. Należy to zrobić bez uwzględniania liczby użytkowników wirtualnych, którzy aktualnie uruchamiają poszczególne testy.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a> Wartość procentowa w oparciu o użytkowników wirtualnych
Ten model testu mieszanego określa procent wirtualnych użytkowników, którzy będą uruchamiać określony test. W przypadku korzystania z tego modelu testu mieszanego następnym testem do uruchomienia jest nie tylko na przypisanych wartościach procentowych, ale również w procentach wirtualnych użytkowników, którzy aktualnie używają określonego testu. W każdym punkcie testu obciążenia liczba użytkowników, którzy uruchamiali określony test, dopasowuje się do przypisanej dystrybucji tak jak to możliwe.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a> Mieszany test tempem

Jeśli określisz test tempem, ustawisz współczynnik wykonywania testów dla każdego wirtualnego użytkownika dla każdego testu w teście mieszanym. Dla każdego testu Ta stawka jest wyrażona jako testy wykonywane przez użytkownika wirtualnego na godzinę. Na przykład można przypisać następujący test tempem do następujących testów:

- A: 4 testy na użytkownika na godzinę

- TestB: 2 testy na użytkownika na godzinę

- TestC: testy 0,125 na użytkownika na godzinę

Jeśli używasz modelu testowego tempem, aparat środowiska uruchomieniowego testu obciążenia gwarantuje, że rzeczywista częstotliwość uruchamiania testów jest mniejsza lub równa określonej szybkości. Jeśli testy są zbyt długie dla przypisanej liczby, zostanie zwrócony błąd.

Ustawienie **czas reakcji między iteracjami testu** nie ma zastosowania, gdy jest używany test tempem.

#### <a name="apply-distribution-to-pacing-delay"></a>Zastosuj rozkład do opóźnienia tempem
Wartość właściwości **Zastosuj dystrybucję do tempem** w scenariuszu testu obciążenia można ustawić na wartość true lub false:

- **Prawda**: w scenariuszu będą stosowane typowe opóźnienia dystrybucji statystycznej określone przez wartość w kolumnie **testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie testu mieszanego** . Aby uzyskać więcej informacji, zobacz [Edit Text mix models, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Załóżmy na przykład, że masz **testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie testu mieszanego** dla testu ustawionego na 2 użytkowników na godzinę. Jeśli właściwość **Zastosuj dystrybucję do tempem** jest ustawiona na **wartość true**, typowa dystrybucja statystyczna jest stosowana do czasu oczekiwania między testami. Testy będą nadal działały 2 testy na godzinę, ale nie musi to być 30 minut między nimi. Pierwszy test może działać po upływie 4 minut, a drugi test po 45 minutach.

- **Fałsz**: testy będą uruchamiane w określonym tempie określonym dla wartości w kolumnie **testy na użytkownika na godzinę** w oknie dialogowym **Edycja testu mieszanego** . Aby uzyskać więcej informacji, zobacz [Edit Text mix models, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Załóżmy na przykład, że masz **testy na użytkownika na godzinę** w oknie dialogowym **Edytowanie testu mieszanego** dla testu ustawionego na 2 użytkowników na godzinę. Jeśli właściwość **Zastosuj dystrybucję do tempem** jest ustawiona na **false (FAŁSZ**), oznacza to, że po uruchomieniu testów nie ma Leeway. Test będzie uruchamiany co 30 minut. Daje to pewność, że wykonujesz 2 testy na godzinę.

  Aby uzyskać więcej informacji, zobacz [jak: stosowanie dystrybucji do opóźnień tempem podczas korzystania z modelu mieszanego testów użycia](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="sequential-order"></a><a name="SequentialOrder"></a> Porządek sekwencyjny
Wybranie opcji kolejność testów sekwencyjnych spowoduje, że każdy użytkownik wirtualny uruchomi wszystkie testy w scenariuszu w kolejności, w jakiej testy zostały zdefiniowane.

## <a name="test-iterations-property"></a>Właściwość iteracji testu
We właściwościach parametrów uruchomieniowych można określić wartość dla właściwości iteracje testu. Ta wartość jest liczbą iteracji testowych do uruchomienia w teście obciążenia. Po rozpoczęciu określonej liczby iteracji testowych nie zostaną uruchomione żadne dodatkowe iteracje testu pomimo ustawień dowolnego profilu ładowania. Po zakończeniu liczby podanych iteracji testowych, test obciążenia kończy się. Aby uzyskać więcej informacji, zobacz [How to: Określanie liczby iteracji testowych w ustawieniu uruchomieniowym](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Zainicjuj i Przerwij testy
Możesz wybrać testy do uruchomienia na początku i na końcu sesji testowania obciążenia każdego użytkownika wirtualnego. Aby uzyskać więcej informacji, zobacz [Edit Text mix models, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Zainicjuj test**. Ten test jest uruchamiany przez każdego użytkownika wirtualnego przed uruchomieniem któregokolwiek z testów w teście mieszanym.

- **Przerwij test**. Ten test jest uruchamiany po uruchomieniu wszystkich testów dla określonego użytkownika wirtualnego.

  Należy zwrócić uwagę na następujące informacje dotyczące testu inicjowania i zakończenia testu:

- Czas trwania testu obciążenia można określić według czasu, a nie liczby iteracji. W tym przypadku po zakończeniu przebiegu testu obciążenia, test zakończenia nie zostanie uruchomiony.

- Jeśli test inicjalizacji jest testem jednostkowym lub testem wydajności sieci Web, stanem TestContext lub WebTestContext, obiekt po zakończeniu testu inicjowania jest zapisywany. Będzie on używany jako kontekst początkowy dla iteracji testów w teście mieszanym.

- Nowi użytkownicy, zgodnie z definicją wyrażoną w procentach właściwości scenariusza nowych użytkowników, zawsze wykonują testy inicjacji, jedną iterację testu z mieszanego testu i zakończenia testu.

## <a name="see-also"></a>Zobacz też

- [Edytuj modele mieszane tekstu, aby określić prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Edytuj wzorce obciążenia, aby modelować działania użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytuj mieszany test, aby określić, które testy należy uwzględnić w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
- [Zmiana modelu testu mieszanego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
