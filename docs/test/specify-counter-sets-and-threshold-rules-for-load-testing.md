---
title: Zestawy liczników i reguły progowe dla testowania obciążenia
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 493295bdbcd1b4906aedf6dca54e264e8ae5e8c6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659954"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia

Testy obciążenia zapewniają nazwane zestawy liczników, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników są zorganizowane według technologii i obejmują aplikacje, ASP.NET, aplikacje platformy .NET, usługi IIS i SQL. Podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**należy dodać początkowy zestaw liczników. Oferują one zestaw wstępnie zdefiniowanych i ważnych zestawów liczników dla testu obciążenia. Zarządzasz licznikami w **Edytor testu obciążeniowego**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat korzystania z maszyn zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zestawy liczników są zbierane na określonych komputerach. Skojarzenie między zestawem liczników a komputerem, który jest używany podczas testu obciążenia, jest *mapą zestawu liczników*. Na przykład serwer sieci Web, który jest testowany, może mieć mapowania zestawów liczników aplikacji ASP.NET, IIS i .NET.

Domyślnie liczniki wydajności są zbierane na kontrolerze i agencie. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Ważne jest, aby dodać testowane serwery do listy komputerów, na których mają być zbierane liczniki. Następnie wszystkie ważne dane systemowe są zbierane i monitorowane podczas testu obciążenia.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Zarządzaj zbiorami liczników dla testu obciążenia:** Po utworzeniu testu obciążenia można edytować zestaw liczników w Edytor testu obciążeniowego. Zarządzanie zbiorami liczników obejmuje wybranie zestawu komputerów, z których mają być zbierane dane dotyczące wydajności, i przypisanie zestawu liczników zbieranych z poszczególnych komputerów. Zarządzasz licznikami w Edytor testu obciążeniowego.|-   [: zarządzanie zbiorami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Dodaj zestawy liczników do testu obciążenia:** Podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Po utworzeniu testu obciążenia można dodać nowe liczniki do istniejących zestawów liczników przy użyciu Edytor testu obciążeniowego.|-   [: Dodawanie liczników do zestawów liczników](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [: Dodawanie niestandardowych zestawów liczników](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Określ regułę progową przy użyciu liczników dla testu obciążenia:** Reguła progu to reguła ustawiona na pojedynczym liczniku wydajności do monitorowania użycia zasobów systemowych podczas testu obciążenia. Definicje zestawu liczników zawierają wstępnie zdefiniowane reguły progów dla wielu kluczowych liczników wydajności. Reguły progowe w testach obciążenia porównują wartość licznika wydajności z wartością stałą lub inną wartością licznika wydajności.|-   [: Dodawanie reguły progu](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Przypisywanie przyjaznych nazw do komputerów, do których są mapowane zestawy liczników:** Można dodać tagi komputera, które umożliwiają zastosowanie łatwej do rozpoznania nazwy na komputerze. Tagi są wyświetlane w węźle **mapowania zestawów liczników** dla drzewa w Edytor testu obciążeniowego. Ważniejsze Tagi są wyświetlane w raportach programu Excel, które pomagają udziałowcom zidentyfikować rolę komputera w teście obciążenia, na przykład "Web serwer1 in lab2" lub "SQL Serwer2 w biurze w Phoenix".<br /><br /> Aby uzyskać więcej informacji, zobacz [raportowanie wyników testów obciążenia dla porównania testów lub analizy trendów](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Korzystanie z zestawów liczników

Narzędzia testu obciążenia zbierają dane wydajności i grafuje je przy użyciu liczników w czasie. Dane licznika są zbierane w interwałach określonych przez użytkownika podczas przebiegu testu obciążenia. Aby uzyskać więcej informacji, zobacz [How to: określ częstotliwość próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Można wyświetlić liczniki w czasie wykonywania lub można je wyświetlić po uruchomieniu testu obciążenia za pomocą *analizatora testu obciążenia*.

Dane liczników są zbierane na serwerze i na dowolnym komputerze, na którym jest uruchamiany test. Jeśli skonfigurowano zestaw komputerów agentów, na których można uruchomić testy, liczniki są również zbierane na tych komputerach.

Istnieją trzy kategorie liczników: wartości procentowe, liczby i średnie. Oto kilka przykładów użycia procesora CPU, SQL Server liczby blokad i żądań usług IIS na sekundę.

![Zestawy liczników testów obciążenia](../test/media/loadtestcountersets.png)

Dane dotyczące wydajności poszczególnych żądań HTTP są zgłaszane przez komputer z uruchomionym testem. takie jak komputer agenta. W przypadku żądań można monitorować dane, takie jak średni czas do pierwszego bajtu, czas odpowiedzi i żądania na sekundę.

Aby ułatwić zbieranie danych wydajności na serwerze sieci Web, Visual Studio Enterprise udostępnia również wstępnie zdefiniowane, nazwane zestawy liczników w oparciu o technologię używaną w testach obciążenia. Te zestawy są przydatne podczas analizowania serwera z uruchomionymi usługami IIS, ASP.NET lub SQL Server. Liczniki, które nie są podane w domyślnym zestawie licznika, można dodać przy użyciu Edytor testu obciążeniowego. Ważne jest, aby dodać komputery lub serwery objęte testem do testu obciążenia, aby upewnić się, że można monitorować użycie zasobów na tych komputerach. Aby uzyskać więcej informacji, zobacz [How to: Manage Counter setss](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Analiza wyników przebiegów ładowania często wymaga znajomości specyficznej dla domeny określonego obszaru, aby wiedzieć, jakie dane mają być zbierane, gdzie można ustawić reguły progów i jak ustalić, kiedy pomiar odzwierciedla określony problem w aplikacji. Aby uzyskać więcej informacji, zobacz [Informacje o regułach progowych](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Zagadnienia dotyczące interwału próbkowania licznika wydajności

Wybierz odpowiednią wartość właściwości **częstotliwość próbkowania** w ustawieniach przebiegu testu obciążenia na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, taka jak domyślna wartość pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. W przypadku dłuższych testów obciążenia zwiększenie szybkości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [How to: określ częstotliwość próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Poniżej przedstawiono niektóre wskazówki dotyczące stawek za próbki.

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\< 1 godz.|5 sekund|
|1 − 8 godzin|15 sekund|
|8 − 24 godz.|30 sekund|
|> 24 godziny|60 sekund|

## <a name="store-performance-data"></a>Przechowywanie danych wydajności

Podczas przebiegu testu obciążenia dane licznika wydajności są zbierane i przechowywane w *repozytorium wyniki testów obciążenia*. Aby uzyskać więcej informacji, zobacz [Zarządzanie wynikami testów obciążenia w repozytorium wyników testów obciążenia](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Reguły progu — informacje

*Reguła progu* to reguła ustawiona na pojedynczym liczniku wydajności do monitorowania użycia zasobów systemowych podczas testu obciążenia. Definicje zestawu liczników zawierają wstępnie zdefiniowane reguły progów dla wielu kluczowych liczników wydajności. Aby uzyskać więcej informacji, zobacz [używanie zestawów liczników do analizowania danych licznika wydajności w testach obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Reguły progów i poziomy

Podczas tworzenia reguł progowych w testach obciążenia należy wybrać dwa typy reguł:

Porównaj stałą &mdash;Compare wartość licznika wydajności z wartością stałą.

Porównaj liczniki &mdash;Compare wartość licznika wydajności z inną wartością licznika wydajności.

Podczas tworzenia reguł progu należy również ustawić poziomy dla reguły. Poziomy to Próg ostrzegawczy i Próg krytyczny. Podczas wyświetlania przebiegu testu obciążenia, naruszenia progu poziomu ostrzeżenia są wskazywane przez żółty symbol, a naruszenia progu poziomu krytycznego są wskazywane przez czerwony symbol.

## <a name="the-alert-if-over-property"></a>Alert, jeśli właściwość przekracza

Ustaw **alert, jeśli właściwość over** ma **wartość true** , aby wskazać, że przyczyną jest przekroczenie progu. Na przykład, jeśli reguła progu jest ustawiona na **czas procesora (%)** , a chcesz otrzymywać alerty, jeśli wartość jest większa niż 90, użyj opcji Porównaj typ reguły **stałej** , ustaw **wartość progu krytycznego** na 90 i Ustaw Alert w **przypadku przekroczenia** wartości **true** .

Ustaw **alert, jeśli właściwość over** ma **wartość false** , aby wskazać, że poniżej wartości progowej występuje problem. Na przykład jeśli reguła progu jest ustawiona na **żądania/s**i chcesz otrzymywać alerty, jeśli wartość jest niższa niż 50, użyj opcji Porównaj typ reguły **stałej** , ustaw **wartość progu krytycznego** na 50 i ustaw **alert, jeśli zostanie przekroczona** wartość **false**.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodawanie reguły progu](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analizowanie naruszeń reguł progu](../test/analyze-threshold-rule-violations-in-load-tests.md)