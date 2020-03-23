---
title: Wzorce obciążenia do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0836fdb085ab33b2a646d9774c94bd859b5ca5ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590309"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego

Właściwości wzorca obciążenia określają sposób dostosowywania symulowanego obciążenia użytkownika podczas testu obciążenia. Visual Studio udostępnia trzy wbudowane wzorce obciążenia: stały, krok i oparte na celach. Wybierz wzorzec obciążenia i dostosować właściwości do odpowiednich poziomów dla celów testu obciążenia.

Wzorzec obciążenia jest składnikiem scenariusza. Scenariusze, wraz z ich zdefiniowanych wzorców obciążenia, obejmują test obciążenia.

> [!NOTE]
> We wszystkich wzorcach obciążenia obciążenie generowane przez program Visual Studio jest symulowanym obciążeniem użytkowników wirtualnych.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Wzorce obciążenia

### <a name="constant"></a>Stały

Wzorzec stałego obciążenia służy do określenia obciążenia użytkownika, który nie zmienia się podczas testu obciążenia. Na przykład po uruchomieniu testu dymu w aplikacji sieci web, można ustawić lekki, stałe obciążenie 10 użytkowników.

#### <a name="constant-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca stałego obciążenia

Wzorzec stałego obciążenia jest używany do uruchamiania tego samego obciążenia użytkownika podczas uruchamiania testu obciążenia. Należy zachować ostrożność przy użyciu wzorca stałego obciążenia, który ma wysoką liczbę użytkowników; może to być nieuzasadnione i nierealistyczne zapotrzebowanie na serwerze lub serwerach na początku testu obciążenia. Na przykład jeśli test obciążenia zawiera test sieci web, który rozpoczyna się od żądania do strony głównej i skonfigurować test obciążenia ze stałym obciążeniem 1000 użytkowników, test obciążenia prześle pierwsze 1000 żądań na stronie głównej tak szybko, jak to możliwe. Może to nie być realistyczna symulacja rzeczywistego dostępu do Twojej witryny. Aby to złagodzić, należy rozważyć użycie wzorzec obciążenia kroku, który zwiększa się stopniowo do 1000 użytkowników lub określić okres rozgrzewania w ustawieniach przebiegu testu obciążenia. Jeśli zostanie określony okres rozgrzewania, test obciążenia automatycznie zwiększa obciążenie stopniowo w okresie rozgrzewania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie opóźnień uruchamiania scenariusza](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Krok

Wzorzec obciążenia kroku służy do określenia obciążenia użytkownika, który zwiększa się z czasem do zdefiniowanego maksymalnego obciążenia użytkownika. W przypadku obciążeń krokowych należy określić **początkową liczbę użytkowników,** **maksymalną liczbę użytkowników,** **czas trwania kroku (sekundy)** i **liczbę kroków użytkownika**.

Na przykład obciążenie kroku z **początkową liczbą użytkowników** jednego, **maksymalna liczba użytkowników** 100, czas trwania kroku **(sekundy)** 10 i **liczba użytkowników kroku** 1 tworzy wzorzec obciążenia użytkownika, który rozpoczyna się od 1, zwiększa się o 1 co 10 sekund, aż osiągnie 100 użytkowników.

> [!NOTE]
> Jeśli całkowity czas trwania testu jest krótszy niż czas wymagany do zwiększenia maksymalnego obciążenia użytkownika, test zatrzymuje się po upływie czasu trwania i nie osiągnie docelowego **maksymalnej liczby użytkowników.**

Można użyć krok cel, aby zwiększyć obciążenie, aż serwer osiągnie punkt, w którym wydajność znacznie spada. Wraz ze wzrostem obciążenia serwerowi w końcu zabraknie zasobów. Obciążenie kroku jest dobrym sposobem, aby określić liczbę użytkowników, w którym występuje. Z obciążeniem krokowym, należy również dokładnie monitorować zasoby agenta, aby upewnić się, że agenci mogą generować żądane obciążenie.

Zwykle należy przeprowadzić kilka przebiegów, które mają różne czasy trwania kroku i krok liczby użytkowników, dzięki czemu można uzyskać dobre pomiary dla danego obciążenia. Często obciążenia pokazują początkowy skok dla każdego kroku, gdy użytkownicy są dodawane. Przytrzymanie obciążenia z tą szybkością pozwala zmierzyć wydajność systemu po odzyskaniu przez system początkowego skoku.

#### <a name="step-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca obciążenia kroków

Wzorzec obciążenia krok może służyć do zwiększenia obciążenia na serwerze lub serwerach w miarę wykonywania testu obciążenia, dzięki czemu można zobaczyć, jak wydajność zmienia się wraz ze wzrostem obciążenia użytkownika. Na przykład, aby zobaczyć, jak serwer lub serwery działają w miarę zwiększania obciążenia użytkownika do 2000 użytkowników, można uruchomić test obciążenia 10-godzinnego przy użyciu wzorca obciążenia kroku, który ma następujące właściwości:

- **Początkowa liczba użytkowników:** 100

- **Maksymalna liczba użytkowników:** 2000

- **Czas trwania kroku (w sekundach)**: 1800

- **Krok Ramp Czas (w sekundach)**: 20

- **Liczba użytkowników kroków:** 100

  Te ustawienia uruchamiają test obciążenia przez 30 minut (1800 sekund) przy obciążeniach użytkownika 100, 200, 300 i do 2000 użytkowników. Właściwość **Step Ramp Time** jest warta szczególnej wzmianki, ponieważ jest to jedyna z tych właściwości, która nie jest dostępna do wyboru w **Kreatorze nowego testu obciążenia.** Ta właściwość umożliwia wzrost z jednego kroku do następnego (na przykład od 100 do 200 użytkowników) występuje stopniowo, a nie natychmiast. W tym przykładzie obciążenie użytkownika zostanie zwiększone ze 100 do 200 użytkowników w okresie 20 sekund (wzrost o pięciu użytkowników co sekundę). Aby uzyskać więcej informacji, zobacz [Jak: Określanie właściwości czasu rampy kroku dla wzorca obciążenia kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Oparte na celach

Wzorzec obciążenia oparty na celu przypomina wzorzec kroku, ale dostosowuje obciążenie użytkownika na podstawie progów licznika wydajności w porównaniu z okresowymi korektami obciążenia użytkownika. Obciążenia oparte na celach są przydatne do różnych celów:

- Maksymalizacja danych wyjściowych z agentów: zmierzyć metrykę ograniczającą klucz na agencie, aby zmaksymalizować wydajność agentów. Zazwyczaj jest to procesor; Jednak może to być również pamięć.

- Osiągnięcie pewnego docelowego poziomu zasobów, zazwyczaj procesora CPU, na serwerze docelowym, a następnie pomiar przepływności na tym poziomie. Dzięki temu można wykonać porównania przepływności do uruchomienia, biorąc pod uwagę spójny poziom użycia zasobów na serwerze.

- Osiągnięcie docelowego poziomu przepływności na serwerze.

  W poniższej tabeli przedstawiono wzorzec oparty na celach z następującymi ustawieniami właściwości:

|Grupa właściwości|Właściwość|Wartość|
|-|--------------|-|
|Licznik wydajności|Kategoria|Procesor|
|Licznik wydajności|Computer (Komputer)|Serwer ContosoServer1|
|Licznik wydajności|Licznik|Czas procesora (%)|
|Licznik wydajności|Wystąpienie|_Total|
|Zakres docelowy dla licznika wydajności|Wysoki koniec|90|
|Zakres docelowy dla licznika wydajności|Niski koniec|70|
|Limity liczby użytkowników|Początkowa liczba użytkowników|1|
|Limity liczby użytkowników|Maksymalna liczba użytkowników|100|
|Limity liczby użytkowników|Maksymalna liczba użytkowników decrement|5|
|Limity liczby użytkowników|Maksymalny przyrost liczby użytkowników|5|
|Limity liczby użytkowników|Minimalna liczba użytkowników|1|

Te ustawienia **powodują,** że analizator testu obciążenia dostosowuje obciążenie użytkownika między 1 a 100 podczas testu w taki sposób, że **licznik** dla `% Processor Time` serwera WebServer01 unosi się między `70%``90%.`

Rozmiar korekty obciążenia każdego użytkownika zależy od ustawień **maksymalnej liczby użytkowników** i **maksymalnej liczby dekrementacji.** Limity liczby użytkowników są ustawiane przez właściwości **Maksymalna liczba użytkowników** i **Minimalna liczba użytkowników.**

#### <a name="goal-based-load-pattern-considerations"></a>Zagadnienia dotyczące wzorca obciążenia opartego na celach

Wzorzec obciążenia oparty na celach jest przydatny, gdy chcesz określić liczbę użytkowników, których system może obsługiwać, zanim osiągnie pewien poziom wykorzystania zasobów. Ta opcja działa najlepiej, gdy już zidentyfikowano zasób ograniczający (czyli wąskie gardło) w systemie.

Załóżmy na przykład, że zasób ograniczający w systemie jest procesorem CPU na serwerze bazy danych i chcesz zobaczyć, ilu użytkowników może być obsługiwanych, gdy procesor CPU na serwerze bazy danych jest zajęty około 75 procentami. Można użyć wzorzec obciążenia opartego na celu, który ma na celu utrzymanie wartości licznika wydajności "%Czas procesora" między 70 procent i 80 procent.

Jedną z rzeczy, na które należy zwrócić uwagę, jest ograniczenie przepływności systemu przez inny zasób. Takie zasoby mogą spowodować, że cel, który jest określony przez wzorzec obciążenia opartego na celu, nigdy nie zostanie osiągnięty. Ponadto obciążenie użytkownika będzie nadal wzrastać, dopóki nie zostanie osiągnięta wartość określona dla **maksymalnej liczby użytkowników.** Zwykle nie jest to pożądane obciążenie, więc należy zachować ostrożność przy wyborze licznika wydajności w wzorzec obciążenia opartego na celu.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Określanie wzorca obciążenia początkowego dla testu obciążenia:** Podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**wybiera się wzorzec obciążenia.|-   [Zmienianie wzorca obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Edytowanie wzorca obciążenia dla testu obciążenia:** Po utworzeniu testu obciążenia można edytować wzorzec obciążenia w **Edytorze testów obciążenia**.|-   [Jak: Określ właściwość czasu rampy kroku dla wzorca obciążenia kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Określanie, czy użytkownicy wirtualni w scenariuszu testu obciążenia powinny zawierać dane pamięci podręcznej sieci Web:** Można zmienić **procent nowych użytkowników** właściwości, aby wpłynąć na sposób, w jaki test obciążenia symuluje buforowanie sieci web, które będą wykonywane przez przeglądarkę sieci web dla użytkowników wirtualnych.|-   [Jak: Określ procent użytkowników wirtualnych korzystających z danych pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Określanie czasu rampy kroku dla wzorca obciążenia kroku:** **Właściwość Step Ramp Time** umożliwia wzrost z jednego kroku do następnego (na przykład od 100 do 200 użytkowników) występuje stopniowo, a nie natychmiast.|-   [Jak: Określ właściwość czasu rampy kroku dla wzorca obciążenia kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Zmienianie wzorca obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości wzorca obciążenia skojarzone ze scenariuszem na poziomy spełniające cele testowe.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testu obciążenia i ich opisy, zobacz [Właściwości scenariusza testu obciążenia.](../test/load-test-scenario-properties.md)

Wzorzec obciążenia określa liczbę aktywnych użytkowników wirtualnych podczas testu obciążenia oraz szybkość dodawania nowych użytkowników. Możesz wybrać jeden z trzech dostępnych wzorców: wzór kroku, stała i oparta na celach. Aby uzyskać więcej informacji, zobacz [Określanie liczby użytkowników wirtualnych z wzorcami obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Właściwości obciążenia można również zmienić programowo za pomocą wtyczki testu obciążenia. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Aby zmienić wzorzec obciążenia

1. Otwórz test obciążenia.

2. W **Edytorze testów obciążenia**w folderze *Scenariusze* rozwiń scenariusz, dla którego chcesz edytować wzorzec obciążenia, i wybierz wzorzec obciążenia dla scenariusza.

    > [!NOTE]
    > Sformułowanie węzła wzorca obciążenia, ponieważ jest on wyświetlany w drzewie scenariuszy testu obciążenia, odzwierciedla profil obciążenia wybrany podczas tworzenia testu obciążenia. Może to być profil **stałego obciążenia** lub **profil obciążenia stopniowego**.

3. Naciśnij **klawisz F4,** aby wyświetlić okno **Właściwości.**

     W oknie **Właściwości** są wyświetlane kategorie **Wzorzec obciążenia** i **Parametry.**

4. (Opcjonalnie) Zmień **właściwość Desek** w kategorii **Wzorzec obciążenia.**

     Dostępne opcje dla właściwości **Wzór** to **Krok,** **Stała**i **Oparta na celu.** Aby uzyskać więcej informacji na temat typów wzorców obciążenia, zobacz [Określanie liczby użytkowników wirtualnych z wzorcami obciążenia w scenariuszu testu obciążenia](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5. (Opcjonalnie) W kategorii **Parametry** zmień wartości.

    > [!NOTE]
    > Wartości, które można ustawić dla **Parametrów** różnią się w zależności od wartości wybranej dla **Pattern** właściwości.

6. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia z nowym wzorcem obciążenia.

## <a name="see-also"></a>Zobacz też

- [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md)
- [Jak: Określ procent użytkowników wirtualnych korzystających z danych pamięci podręcznej sieci Web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Jak: Określ właściwość czasu rampy kroku dla wzorca obciążenia kroku](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)
