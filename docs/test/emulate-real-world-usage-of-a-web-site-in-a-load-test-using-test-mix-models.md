---
title: Emulacja wykorzystanie w świecie rzeczywistym witryny sieci Web do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 87161a4d58411f5f1bbe0347d093a39f17742bd6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042070"
---
# <a name="emulate-expected-real-world-usage-of-a-website-or-application-in-a-load-test-using-a-test-mix-model"></a>Emulowanie oczekiwanego wykorzystania rzeczywistych witryny sieci Web lub aplikacji w teście obciążenia przy użyciu modelu testu mieszanego

Załaduj opcje modelowania umożliwia bardziej dokładnie przewidzieć oczekiwane wykorzystanie w świecie rzeczywistym witryny sieci Web lub aplikacji, które obciążenia testujesz. Należy to zrobić, ponieważ test obciążenia, który nie jest oparty na dokładne ładowanie modelu można wygenerować wyświetlenie nieprawdziwych wyników.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Test mieszany modelu rozszerzeń

Za pomocą edytora testu obciążenia lub Kreator modelu testu mieszanego, można określić następujące rodzaje test mieszany w scenariuszu testu obciążenia. Aby uzyskać więcej informacji, zobacz [zmienić model testu mieszanego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Można określić jedną z następujących opcji model testu mieszanego, dla scenariusza testu obciążenia:

- **Na podstawie całkowitej liczby testów:** Określa, który test wydajności lub jednostki w sieci web jest uruchamiany, gdy wirtualny użytkownik rozpoczyna iterację testu. Na końcu testu obciążeniowego ile razy określonego testu dopasować rozkład testu przypisane. Ten model testu mieszanego należy użyć, gdy test mieszany jest tworzony na transakcji, określonym w dzienniku IIS lub w danych produkcyjnych. Aby uzyskać więcej informacji, zobacz [wartość procentową na podstawie testów rozpoczęte](#BasedOnTestsStarted).

- **Na podstawie liczby wirtualnych użytkowników:** Określa procent wirtualnych użytkowników, którzy uruchomią namierzenie internetowego testu wydajności lub jednostki. W dowolnym momencie testu obciążeniowego liczbę użytkowników, którzy uruchomili określonego testu pasuje do przypisanego rozkładu. Ten model testu mieszanego należy użyć, gdy test mieszany jest tworzony na procent użytkowników, którzy uruchomili określonego testu. Aby uzyskać więcej informacji, zobacz [wartość procentową na podstawie liczby użytkowników wirtualnych](#PercentageBasedonVirtualUsers).

- **Na podstawie tempa użytkownika:** W trakcie testu obciążenia każdy test wydajności sieci web lub test jednostkowy jest uruchamiany określoną liczbę razy na użytkowników, na godzinę. Ten model testu mieszanego należy użyć, jeśli chcesz, aby wirtualni użytkownicy uruchamiali test w konkretnym tempie przez cały test obciążeniowy. Aby uzyskać więcej informacji, zobacz [Pacing test mieszany](#PacingTestMix).

    > [!TIP]
    > Kiedy należy wybrać **procent test mieszany** i gdy użytkownik wybierze **wartość procentową na podstawie liczby użytkowników wirtualnych**? Różnica między te dwie opcje ważne jest, gdy niektóre testy w asortymencie test ma znacznie dłuższy czas niż inne testy. W takiej sytuacji należy prawdopodobnie wybrać **wartość procentową na podstawie liczby użytkowników wirtualnych**. Ten wybór pomaga uniknąć przebieg testu, w którym zwiększa prawdopodobieństwo, że zbyt wielu użytkowników będą uruchomione testy czas trwania długiej. Jednak jeśli wszystkie testy mają podobne czasów trwania, bezpieczniej można **procent test mieszany**.

- **Oparte na kolejności:** Każdy wirtualny użytkownik uruchamia testy wydajności lub jednostki sieci web, w kolejności, że testy są zdefiniowane w tym scenariuszu. Wirtualny użytkownik kontynuuje, okrągło testów w następującej kolejności do czasu ukończenia testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [kolejności sekwencyjnej](#SequentialOrder).

### <a name="BasedOnTestsStarted"></a> Procent opartych na rozpoczętych testów
 Dla każdego testu w zestawie można określić wartość procentową, która określa, jak często testu jest wybrany jako następny test do uruchomienia. Na przykład można przypisać następujące wartości procentowe do trzech testów:

- TestA (50%)

- TestB (35%)

- TestC (15%)

  Jeśli używasz tego ustawienia, Następny test, aby rozpocząć opiera się na przypisane wartości procentowe. W tym nie biorąc pod uwagę liczbę wirtualnych użytkowników, którzy są aktualnie uruchomione każdego testu.

### <a name="PercentageBasedonVirtualUsers"></a> Wartość procentową na podstawie liczby użytkowników wirtualnych
 Ten model testu mieszanego Określa procent wirtualnych użytkowników, którzy uruchomią określonego testu. Jeśli używasz tego modelu testu mieszanego, Następny test, aby rozpocząć opiera się nie tylko na przypisane wartości procentowych, ale także na procent wirtualnych użytkowników, którzy są aktualnie uruchomione określonego testu. W dowolnym momencie testu obciążeniowego liczbę użytkowników, którzy uruchomili określonego testu możliwie najdokładniej pasuje do przypisanego rozkładu.

### <a name="PacingTestMix"></a> Tempo testu mieszanego
 Jeśli określisz pacing mieszanki testów, możesz ustawić wskaźnik wykonania testu dla każdego wirtualnego użytkownika dla każdego testu w teście mieszanym. Dla każdego testu ten kurs jest wyrażona jako testy na wirtualnego użytkownika na godzinę. Na przykład może przypisywać pacing się test mieszany, do następujących testów:

- TestA: 4 testy na użytkownika na godzinę

- TestB: 2 testy na użytkownika na godzinę

- TestC: 0,125 testy na użytkownika na godzinę

  Jeśli używasz pacing model testu mieszanego, aparat środowiska uruchomieniowego testu obciążenia gwarantuje, że rzeczywista szybkość uruchamiania testów jest mniejsza lub równa określonej szybkości. Jeśli testy są uruchamiane zbyt długo dla przypisany numer należy wykonać, jest zwracany błąd.

  **Traktować czas między iteracjami testu** ustawienie nie ma zastosowania, gdy używasz pacing testu mieszanego.

#### <a name="apply-distribution-to-pacing-delay"></a>Zastosuj rozkład do opóźnienia do
 Wartość **dystrybucji Zastosuj rozkład do opóźnienia** właściwość w scenariuszu testu obciążenia można ustawić na wartość true lub false:

- **Wartość true,**: Scenariusz będzie stosowane typowe rozkłady statystyczne opóźnienia, określony przez wartość w **testy na użytkownika na godzinę** kolumny w **Edytuj Test mieszany** okna dialogowego. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Na przykład załóżmy, że masz **testy na użytkownika na godzinę** wartość w **Edytuj Test mieszany** okno dialogowe dla testu równa 2 użytkowników na godzinę. Jeśli **dystrybucji Zastosuj rozkład do opóźnienia** właściwość jest ustawiona na **True**, typowe rozkład statystyczny jest stosowany do czasu oczekiwania między testy. Testy będą nadal działać 2 testy na godzinę, ale nie będzie zawsze 30 minut między nimi. Pierwszy test, może uruchomić po 4 minut, a drugi test po 45 minut.

- **FALSE**: Testy zostaną uruchomione w tempie określonych określony na potrzeby wartości **testy na użytkownika na godzinę** kolumny w **Edytuj Test mieszany** okna dialogowego. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Na przykład załóżmy, że masz **testy na użytkownika na godzinę** wartość w **Edytuj Test mieszany** okno dialogowe dla testu równa 2 użytkowników na godzinę. Jeśli **dystrybucji Zastosuj rozkład do opóźnienia** właściwość jest ustawiona na **False**, po prostu spowoduje nadanie nie swobodę uruchamiania testów. Test zostanie uruchomiony co 30 minut. Dzięki temu wykonywania testów 2 / godz.

  Aby uzyskać więcej informacji, zobacz [jak: Zastosuj rozkład opóźnienia, korzystając z tempa model testu mieszanego użytkownika do](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="SequentialOrder"></a> Kolejności
 Wybieranie oparty na test sekwencyjnych order — opcja sprawia, że każdy użytkownik wirtualny Uruchom wszystkie testy w ramach scenariusza opisywanego w kolejności, że testy zostały zdefiniowane.

## <a name="test-iterations-property"></a>Właściwość iteracji testu
 We właściwościach parametrów uruchomieniowych można określić wartość dla właściwości iteracji testu. Ta wartość jest liczba iteracji testu do uruchomienia w teście obciążeniowym. Po rozpoczęciu określonej liczby iteracji testowych nie dodatkowych iteracjami zostanie uruchomiony niezależnie od ustawienia profilom obciążenia. Po ukończeniu liczby iteracji testowych, które określono kończy się testu obciążenia. Aby uzyskać więcej informacji, zobacz [jak: Określanie liczby iteracji testowych w ustawieniach testu](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Testy rozpoczęcia i zakończenia
 Możesz wybrać testy do uruchomienia na początku i na końcu sesji testowania obciążenia, każdy użytkownik wirtualny. Aby uzyskać więcej informacji, zobacz [edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Inicjowanie testu**. Ten test jest wykonywany przez każdy użytkownik wirtualny, przed wykonaniem dowolnego z testów w teście mieszanym.

- **Test zakończenia**. Ten test jest uruchamiany po uruchomieniu wszystkich testów dla danego użytkownika wirtualnego.

  Należy pamiętać, następujące kwestie dotyczące test rozpoczęcia i zakończenia testu:

- Czas trwania testu obciążenia można określić czasu, a nie według liczby iteracji. W takim przypadku po zakończeniu czasu trwania przebiegu testu obciążeniowego test zakończenia nie zostanie uruchomiona.

- W przypadku testu jednostkowego lub testu wydajności sieci web test rozpoczęcia stan obiektu TestContext lub WebTestContext, po zakończeniu inicjowania testu są zapisywane. Go następnie posłuży jako kontekst początkowy dla iteracji testów w teście mieszanym.

- Nowych użytkowników, zgodnie z definicją we właściwości scenariusza procent dla nowych użytkowników, zawsze wykonać test rozpoczęcia, jednej iteracji testu z test mieszany i test zakończenia.

## <a name="see-also"></a>Zobacz także

- [Edytowanie modeli testów mieszanych w celu określania prawdopodobieństwa użytkownik wirtualny uruchomi testu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Edytowanie wzorców obciążenia w celu modelu aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Edytuj test mieszany, aby określić, które testy, aby uwzględnić w scenariuszu testu obciążenia](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
- [Zmień model testu mieszanego w scenariuszu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)