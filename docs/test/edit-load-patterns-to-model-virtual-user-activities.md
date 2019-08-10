---
title: Wzorce obciążenia do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5459f1b82dd83905f2672d198f503a741778287b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926534"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Edytuj wzorce obciążenia, aby modelować działania użytkownika wirtualnego

Właściwości wzorca obciążenia określają sposób, w jaki symulowane obciążenie użytkownika jest dostosowywane podczas testu obciążenia. Program Visual Studio oferuje trzy wbudowane wzorce obciążeń: stałą, krok i oparty na celach. Wybór wzorca obciążenia i dostosowanie właściwości do odpowiednich poziomów dla celów testów obciążenia.

Wzorzec obciążenia jest składnikiem scenariusza. Scenariusze, wraz ze zdefiniowanymi wzorcami obciążenia, składają się na test obciążenia.

> [!NOTE]
> We wszystkich wzorcach obciążenia, obciążenie generowane przez program Visual Studio jest symulowanym obciążeniem wirtualnych użytkowników.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Wzorce obciążenia

### <a name="constant"></a>Stała

Wzorzec obciążenia stałego służy do określania obciążenia użytkownika, które nie zmienia się podczas testu obciążenia. Na przykład po uruchomieniu testu dymu w aplikacji sieci Web może zajść potrzeba ustawienia światła, stałego obciążenia 10 użytkowników.

#### <a name="constant-load-pattern-considerations"></a>Zagadnienia dotyczące wzorców stałych obciążeń

Wzorzec obciążenia stałego jest używany do uruchamiania tego samego obciążenia użytkownika podczas przebiegu testu obciążenia. Należy zachować ostrożność przy użyciu stałego wzorca obciążenia, który ma dużą liczbę użytkowników; takie działanie może spowodować nieuzasadnione i nierealistyczne zapotrzebowanie na serwerze lub serwerach na początku testu obciążenia. Na przykład jeśli test obciążenia zawiera test sieci Web, który rozpoczyna się od żądania do strony głównej, a następnie zostanie skonfigurowany test obciążenia ze stałym obciążeniem 1 000 użytkowników, test obciążenia przekaże pierwsze żądania 1 000 do strony głównej tak szybko, jak to możliwe. Może to nie być realistyczna symulacja rzeczywistego dostępu do witryny sieci Web. Aby rozwiązać ten problem, należy rozważyć użycie etapu wzorca obciążenia, który zwiększa stopniowo do 1 000 użytkowników, lub określa okres rozgrzewania w ustawieniach przebiegu testu obciążenia. Jeśli zostanie określony okres rozgrzewania, test obciążenia automatycznie zwiększy obciążenie stopniowo w okresie rozgrzewania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariusza](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Krok

Wzorzec obciążenia etapów służy do określania obciążenia użytkownikami, które zwiększa się wraz z czasem do zdefiniowanego maksymalnego obciążenia użytkownikami. W przypadku obciążeń krokowych należy określić **początkową liczbę użytkowników**, **maksymalną liczbę użytkowników**, **czas trwania kroku (sekundy)** i **liczbę kroków użytkownika**.

Przykładowo obciążenie etapem z **początkową liczbą użytkowników** o wartości 1 **, Maksymalna liczba użytkowników** wynoszącą 100, **czas trwania kroku (w sekundach)** o wartości 10, a **Liczba użytkowników** w ramach kroku wynoszący% tworzy wzorzec obciążenia użytkownika, który rozpoczyna się od 1, zwiększa się o 1 co 10 sekund do czasu osiągnie 100 użytkowników.

> [!NOTE]
> Jeśli łączny czas trwania testu jest krótszy niż czas wymagany do osiągnięcia maksymalnego obciążenia przez użytkownika, test zakończy się po upływie czasu trwania i nie osiągnie maksymalnej wartości docelowej **liczby użytkowników** .

Możesz użyć celu, aby zwiększyć obciążenie, dopóki serwer osiągnie moment, w którym wydajność znacznie się zmniejsza. Po zwiększeniu obciążenia serwer ostatecznie zabraknie zasobów. Obciążenie krokami jest dobrym sposobem na określenie liczby użytkowników, w których występuje. Obciążenie krok po kroku umożliwia również monitorowanie zasobów agentów w celu upewnienia się, że agenci mogą generować żądane obciążenie.

Zwykle należy przeprowadzić kilka przebiegów, które mają różne czasy trwania i krokowe liczby użytkowników, dzięki czemu można uzyskać dobre pomiary dla danego obciążenia. Często ładunki zawierają początkowy skok dla każdego kroku, gdy użytkownicy są dodawani. Utrzymywanie obciążenia z tą szybkością pozwala mierzyć wydajność systemu po odzyskaniu przez system od początkowego przeskoku.

#### <a name="step-load-pattern-considerations"></a>Zagadnienia dotyczące wzorców ładowania kroków

Wzorzec obciążenia krokami może służyć do zwiększenia obciążenia serwera lub serwerów w miarę przebiegu testu obciążenia, aby zobaczyć, jak wydajność zmienia się wraz ze wzrostem obciążenia użytkownika. Na przykład, aby zobaczyć, jak serwer lub serwery działają wraz ze wzrostem obciążenia użytkownika do 2 000 użytkowników, można uruchomić 10-godzinny test obciążenia przy użyciu wzorca obciążenia krokowego, który ma następujące właściwości:

- **Początkowa liczba użytkowników**: 100

- **Maksymalna liczba użytkowników**: 2000

- **Czas trwania kroku (w sekundach)** : 1 800

- **Czas pochylenia kroku (w sekundach)** : 20

- **Liczba użytkowników kroku**: 100

  Te ustawienia uruchamiają test obciążenia przez 30 minut (1 800 sekund) na obciążeniach użytkowników 100, 200, 300 i do 2 000. Właściwość **czas rampy kroku** jest warta szczególna wzmianki, ponieważ jest to jedyna z tych właściwości, które nie są dostępne do wyboru w **nowym Kreator testu obciążeniowego**. Ta właściwość pozwala na stopniowe przechodzenie między kolejnymi krokami (na przykład od 100 do 200 użytkowników). W tym przykładzie obciążenie użytkownikami zostanie zwiększone od 100 do 200 użytkowników w ciągu 20 sekund (co dwa w drugim okresie). Aby uzyskać więcej informacji, zobacz [jak: Określ właściwość czas rampy kroku dla wzorca](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)obciążenia kroku.

### <a name="goal-based"></a>Oparte na celach

Wzorzec obciążenia oparty na celach przypomina wzorzec kroku, ale dostosowuje obciążenie użytkowników na podstawie progów licznika wydajności, a okresowe korekty obciążenia użytkownika. Obciążenia oparte na celach są przydatne w różnych celach:

- Maksymalizowanie danych wyjściowych z agentów: Zmierz metrykę ograniczającą klucz agenta w celu zmaksymalizowania danych wyjściowych agentów. Zwykle jest to procesor CPU; Może to jednak również być pamięć.

- Dotarcie do jakiegoś docelowego poziomu zasobów, zazwyczaj procesora CPU, na serwerze docelowym, mierząc przepływność na tym poziomie. Pozwala to na uruchamianie porównań z przepływem pracy z uwzględnieniem spójnego poziomu użycia zasobów na serwerze.

- Osiągnięcie docelowego poziomu przepływności na serwerze.

  W poniższej tabeli przedstawiono przykład przedstawiający wzorzec oparty na celach o następujących ustawieniach właściwości:

|Grupa właściwości|Właściwość|Wartość|
|-|--------------|-|
|Licznik wydajności|Kategoria|Procesor|
|Licznik wydajności|Computer|ContosoServer1|
|Licznik wydajności|Licznik|Czas procesora (%)|
|Licznik wydajności|Wystąpienie|_Total|
|Zakres docelowy dla licznika wydajności|Duże zakończenie|90|
|Zakres docelowy dla licznika wydajności|Niski koniec|70|
|Limity liczby użytkowników|Początkowa liczba użytkowników|1|
|Limity liczby użytkowników|Maksymalna liczba użytkowników|100|
|Limity liczby użytkowników|Maksymalna liczba użytkowników zmniejsza|5|
|Limity liczby użytkowników|Maksymalny przyrost liczby użytkowników|5|
|Limity liczby użytkowników|Minimalna liczba użytkowników|1|

Te ustawienia powodują, że **Analizator testu obciążenia** dostosowuje obciążenie użytkownika między 1 a 100 podczas przebiegu testowego w taki sposób, że `% Processor Time` licznik webserver01 jest aktywowany między `70%` i`90%.`

Rozmiar każdej korekty obciążenia użytkownika zależy od maksymalnego przyrostu **liczby** użytkowników i maksymalnego **zmniejszenia liczby użytkowników** . Limity liczby użytkowników są ustawiane przez **maksymalną liczbę** użytkowników i **minimalne właściwości liczby użytkowników** .

#### <a name="goal-based-load-pattern-considerations"></a>Zagadnienia dotyczące wzorców obciążenia opartego na celach

Wzorzec obciążenia oparty na celach jest przydatny, gdy chcesz określić liczbę użytkowników, których system może obsłużyć, zanim osiągnie jakiś poziom wykorzystania zasobów. Ta opcja działa najlepiej, gdy zidentyfikowano już zasób ograniczający (czyli wąskie gardło) w systemie.

Załóżmy na przykład, że jest wiadomo, że zasób ograniczający w systemie jest procesorem CPU na serwerze bazy danych, i chcesz sprawdzić, ilu użytkowników może być obsługiwanych, gdy procesor na serwerze bazy danych jest około 75 procent zajętości. Można użyć wzorca obciążenia opartego na celach, który ma na celu utrzymanie wartości licznika wydajności "czas procesora" (%) między 70% i 80%.

Jednym z rzeczy, które należy obserwować, jest to, że jakiś inny zasób ogranicza przepływność systemu. Takie zasoby mogą spowodować, że cel określony przez wzorzec obciążenia oparty na celach nie zostanie nigdy osiągnięty. Ponadto obciążenie użytkownikami będzie stale wzrastać, dopóki wartość określona dla **maksymalnej liczby użytkowników** zostanie osiągnięta. Zwykle nie jest to wymagane obciążenie, dlatego należy zachować ostrożność w przypadku wyboru licznika wydajności w wzorcu obciążenia opartym na celach.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Określanie początkowego wzorca obciążenia dla testu obciążenia:** Podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**należy wybrać wzorzec obciążenia.|-   [Zmiana wzorca obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Edytowanie wzorca obciążenia dla testu obciążenia:** Po utworzeniu testu obciążenia można edytować wzorzec obciążenia w **Edytor testu obciążeniowego**.|-   [Jak: Określ właściwość czasu rampy kroku dla wzorca ładowania kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Określanie, czy wirtualne użytkownicy w scenariuszu testu obciążenia powinny zawierać dane z pamięci podręcznej sieci Web:** Można zmienić **wartość procentowa właściwości New Users** , aby mieć wpływ na sposób, w jaki test obciążenia symuluje buforowanie sieci Web, które byłyby wykonywane przez przeglądarkę sieci Web dla użytkowników wirtualnych.|-   [Jak: Określ wartość procentową użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Określanie czasu rampy kroku dla wzorca obciążenia krokami:** Właściwość **czas rampy kroku** pozwala zwiększyć się od jednego kroku do następnego (na przykład od 100 do 200 użytkowników), a nie od razu.|-   [Jak: Określ właściwość czasu rampy kroku dla wzorca ładowania kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Zmiana wzorca obciążenia

Po utworzeniu testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości wzorca obciążenia powiązane z scenariuszem na poziomy spełniające cele testów.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

Wzorzec obciążenia określa liczbę wirtualnych użytkowników aktywnych podczas testu obciążenia i szybkość dodawania nowych użytkowników. Można wybierać spośród trzech dostępnych wzorców: wzorzec kroku, stała i cel na podstawie. Aby uzyskać więcej informacji, zobacz [Określanie liczby wirtualnych użytkowników ze wzorcami obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Możesz również programowo zmienić właściwości obciążenia za pomocą wtyczki testu obciążenia. Aby uzyskać więcej informacji, zobacz [jak: Utwórz wtyczkę](../test/how-to-create-a-load-test-plug-in.md)testu obciążenia.

### <a name="to-change-the-load-pattern"></a>Aby zmienić wzorzec obciążenia

1. Otwórz test obciążenia.

2. W **Edytor testu obciążeniowego**w folderze *scenariusze* rozwiń scenariusz, dla którego chcesz edytować wzorzec obciążenia i wybierz wzorzec obciążenia dla scenariusza.

    > [!NOTE]
    > Tekst węzła wzorca obciążenia, który jest wyświetlany w drzewie scenariuszy testu obciążenia, odzwierciedla profil obciążenia, który został wybrany podczas tworzenia testu obciążenia. Może to być **profil stałego ładowania** lub **krok ładowania**.

3. Naciśnij klawisz **F4** do wyświetlenia **właściwości** okna.

     **Wzorzec obciążenia** i kategorie **parametrów** są wyświetlane w oknie **Właściwości** .

4. Obowiązkowe Zmień właściwość **wzorzec** w kategorii **wzorzec obciążenia** .

     Wybór właściwości **wzorzec** to **etap**, **stała**i **cel na podstawie**. Aby uzyskać więcej informacji na temat typów wzorców obciążenia, zobacz [Określanie liczby wirtualnych użytkowników ze wzorcami obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5. Obowiązkowe W kategorii **Parametry** Zmień wartości.

    > [!NOTE]
    > Wartości, które można ustawić dla **parametrów** , różnią się w zależności od wartości wybranej dla właściwości **wzorzec** .

6. Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie można uruchomić test obciążenia z nowym wzorcem obciążenia.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Instrukcje: Określ wartość procentową użytkowników wirtualnych korzystających z danych w pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Instrukcje: Określ właściwość czasu rampy kroku dla wzorca ładowania kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)