---
title: Zestawy liczników i reguły progowe do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 440bc01b52269c477d9d2f2194fd831041f1d20d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596323"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia

Testy obciążenia zapewniają nazwane zestawy liczników, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników są zorganizowane według technologii i obejmują aplikacje, ASP.NET, aplikację .NET, usługi IIS i SQL. Podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**należy dodać początkowy zestaw liczników. Oferują one zestaw wstępnie zdefiniowanych i ważnych zestawów liczników dla testu obciążenia. Liczniki można zarządzać w **Edytorze testów obciążenia**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat korzystania z komputerów zdalnych w teście obciążenia, zobacz [Kontrolery testów i agenci testowi.](configure-test-agents-and-controllers-for-load-tests.md)

Zestawy liczników są zbierane na określonych komputerach. Skojarzenie między zestawem liczników a komputerem używanym podczas testu obciążenia jest *mapą zestawu liczników*. Na przykład testowany serwer sieci web może mieć ASP.NET, usługi IIS i .NET mapowania zestawów liczników aplikacji.

Domyślnie liczniki wydajności są zbierane na kontrolerze i agentach. Aby uzyskać więcej informacji, zobacz [Kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

Ważne jest, aby dodać serwery testowe do listy komputerów, na których mają być zbierane liczniki. Następnie wszystkie ważne dane systemowe są zbierane i monitorowane podczas testu obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Zarządzanie zestawami liczników dla testu obciążenia:** Po utworzeniu testu obciążenia można edytować zestaw liczników w Edytorze testów obciążenia. Zarządzanie zestawami liczników polega na wyborze zestawu komputerów, z których mają być zbierane dane dotyczące wydajności, oraz na przypisywaniu zestawu zestawów liczników do zbierania z każdego komputera. Liczniki można zarządzać w Edytorze testów obciążenia.|-   [Jak: Zarządzanie zestawami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Dodaj zestawy liczników do testu obciążenia:** Podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Po utworzeniu testu obciążenia można dodać nowe liczniki do istniejących zestawów liczników za pomocą Edytora testów obciążenia.|-   [Jak: Dodawanie liczników do zestawów liczników](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Jak: Dodawanie niestandardowych zestawów liczników](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Określ regułę progową przy użyciu liczników dla testu obciążenia:** Reguła progu jest regułą ustawioną na liczniku wydajności dla poszczególnych użytkowników systemu w celu monitorowania użycia zasobów systemowych podczas testu obciążenia. Definicje zestawów liczników zawierają wstępnie zdefiniowane reguły progowe dla wielu kluczowych liczników wydajności. Reguły progowe w testach obciążenia porównują wartość licznika wydajności z wartością stałą lub inną wartością licznika wydajności.|-   [Jak: Dodawanie reguły progowej](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Przypisywanie przyjaznych nazw do komputerów, na których są mapowane zestawy liczników:** Można dodać znaczniki komputera, które umożliwiają zastosowanie łatwo rozpoznawanej nazwy do komputera. Znaczniki są wyświetlane w węźle **Mapowania zestawów liczników** dla drzewa w Edytorze testów obciążenia. Co ważniejsze, znaczniki są wyświetlane w raportach programu Excel, które pomagają zainteresowanym stronom określić rolę komputera w teście obciążenia, na przykład "Web Server1 w lab2" lub "SQL Server2 w biurze Phoenix".<br /><br /> Aby uzyskać więcej informacji, zobacz [Raport wyników testów obciążenia dla porównań testów lub analizy trendów](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Używanie zestawów liczników

Narzędzia do testowania obciążenia zbierają dane o wydajności i wykresują przy użyciu liczników w czasie. Dane licznika są zbierane w odstępach czasu określonych przez użytkownika podczas przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [Jak: Określanie częstotliwości próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Liczniki można wyświetlać w czasie wykonywania lub można je wyświetlić po uruchomieniu testu obciążenia przy użyciu *analizatora testów obciążenia*.

Dane licznika są zbierane na serwerze i na dowolnym komputerze, na którym jest uruchamiany test. Jeśli skonfigurowano zestaw komputerów agenta, na których mają być uruchamiane testy, liczniki są zbierane również na tych komputerach.

Istnieją trzy kategorie liczników: wartości procentowe, liczby i średnie. Niektóre przykłady to % użycia procesora CPU, liczba blokad programu SQL Server i żądania usług IIS na sekundę.

![Zestawy liczników testu obciążenia](../test/media/loadtestcountersets.png)

Dane dotyczące wydajności dla poszczególnych żądań HTTP są zgłaszane przez komputer, który uruchamia test. takich jak komputer agenta. W przypadku żądań można monitorować dane, takie jak średni czas do pierwszego bajtu, czas odpowiedzi i żądania na sekundę.

Aby ułatwić zbieranie danych o wydajności na serwerze sieci web, program Visual Studio Enterprise udostępnia również wstępnie zdefiniowane, nazwane zestawy liczników, oparte na technologii do użycia w testach obciążenia. Zestawy te są przydatne podczas analizowania serwera z uruchomionymi usługami IIS, ASP.NET lub SQL Server. Liczniki nie podano w domyślnym zestawie liczników można dodać za pomocą Edytora testów obciążenia. Ważne jest, aby dodać komputery lub serwery w testach obciążenia, aby upewnić się, że można monitorować użycie zasobów na tych komputerach. Aby uzyskać więcej informacji, zobacz [Jak: Zarządzanie zestawami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Analiza wyników przebiegów obciążenia często wymaga znajomości określonego obszaru w danej domenie, aby wiedzieć, jakie dane mają być zbierane, gdzie ustawić reguły progowe i jak określić, kiedy pomiar odzwierciedla określony problem w aplikacji. Aby uzyskać więcej informacji, zobacz [Informacje o regułach progowych](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Zagadnienia interwału próbkowania licznika wydajności

Wybierz odpowiednią wartość dla **Sample Rate** właściwości w ustawieniach przebiegu testu obciążenia na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, taka jak wartość domyślna wynosząca pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. W przypadku dłuższych testów obciążenia zwiększenie częstotliwości próbkowania zmniejsza ilość zebranych danych. Aby uzyskać więcej informacji, zobacz [Jak: Określanie częstotliwości próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Poniżej przedstawiono kilka wskazówek dotyczących stawek próbek.

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\<1 godz.|5 sekund|
|1−8 godzin|15 sekund|
|8−24 godziny|30 sekund|
|> 24 godziny|60 sekund|

## <a name="store-performance-data"></a>Przechowywanie danych o wydajności

Podczas testu obciążenia dane licznika wydajności są zbierane i przechowywane w *repozytorium wyników testu obciążenia*. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testu obciążenia w repozytorium wyników testu obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Informacje o regułach progowych

*Reguła progu* jest regułą ustawioną na liczniku wydajności dla poszczególnych użytkowników systemu w celu monitorowania użycia zasobów systemowych podczas testu obciążenia. Definicje zestawów liczników zawierają wstępnie zdefiniowane reguły progowe dla wielu kluczowych liczników wydajności. Aby uzyskać więcej informacji, zobacz [Używanie zestawów liczników w celu analizowania danych licznika wydajności w testach obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Zasady i poziomy progowe

Podczas tworzenia reguł progowych w testach obciążenia należy wybrać jeden z dwóch typów reguł:

Porównaj&mdash;stałą Porównaj wartość licznika wydajności ze stałą wartością.

Porównaj&mdash;liczniki Porównaj wartość licznika wydajności z inną wartością licznika wydajności.

Podczas tworzenia reguł progowych można również ustawić poziomy dla reguły. Poziomy są próg ostrzegawczy i próg krytyczny. Podczas wyświetlania przebiegu testu obciążenia naruszenia progu poziomu ostrzeżenia są oznaczone żółtym symbolem, a naruszenia progu poziomu krytycznego są oznaczone czerwonym symbolem.

## <a name="the-alert-if-over-property"></a>Właściwość Alert If Over

Ustaw **alert, jeśli over** właściwość **true,** aby wskazać, że przekroczenie progu jest problem. Jeśli na przykład reguła progowa jest ustawiona na **% czasu procesora**i chcesz otrzymywać alerty, jeśli wartość jest większa niż 90, użyj typu **reguły Porównaj stałą,** ustaw **wartość progu krytycznego** na 90 i ustaw **alert Jeśli na** **wartość true**.

Ustaw **alert, jeśli over** właściwość **false,** aby wskazać, że spada poniżej progu jest problem. Jeśli na przykład reguła progowa jest ustawiona na **żądania/s**i chcesz otrzymywać alerty, jeśli wartość jest niższa niż 50, użyj typu **reguły Porównaj stałą,** ustaw **wartość progu krytycznego** na 50 i ustaw **alert Jeśli powyżej** na **False**.

## <a name="see-also"></a>Zobacz też

- [Jak: Dodawanie reguły progowej](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analizowanie naruszeń reguł progowych](../test/analyze-threshold-rule-violations-in-load-tests.md)
