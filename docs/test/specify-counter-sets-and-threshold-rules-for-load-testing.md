---
title: Licznik zestawów oraz zasad progu dla testowania obciążenia
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3cbdd30022b521803662f18b8d3438c6b1ddb37c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057421"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym

Testy obciążenia dostarczają nazwanych zestawów licznika, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników są uporządkowane według technologii i obejmują aplikacji, ASP.NET, aplikację platformy .NET, usługi IIS i SQL. Po utworzeniu testu obciążenia przy użyciu **Kreatora nowego testu obciążeniowego**, jest dodawany początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych i ważnych liczników dla testu obciążeniowego zestaw. Zarządzasz licznikami w **edytora testu obciążenia**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji o sposobie używania komputerów zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zestawy liczników są zbierane na komputerach, należy określić. Skojarzenie między zestawem liczników a komputerem, który jest używany podczas testu obciążeniowego jest *mapy zestaw liczników*. Na przykład serwer sieci web, która jest testowana Niewykluczone, ASP.NET, IIS i mapowania zbiorów liczników platformy .NET.

Domyślnie liczniki wydajności są zbierane na kontroler i agentów. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Należy dodać serwery w ramach testu do listy komputerów, na których można zebrać liczników. Następnie wszystkie dane systemowe jest zbierane i monitorowane podczas testu obciążeniowego.

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Zarządzanie zbiorami liczników dla testu obciążeniowego:** po utworzeniu testu obciążenia, można edytować zestaw liczników w edytorze testu obciążeniowego. Zarządzanie zbiorami liczników obejmuje, wybierając zestaw komputerów, z których chcesz zbierać dane dotyczące wydajności i przypisywanie zbiór zestawów liczników, które mają być zbierane z każdego komputera. Zarządzasz licznikami w edytorze testu obciążenia.|-   [Porady: Zarządzanie zbiorami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Dodawanie zestawów liczników do testu obciążeniowego:** podczas tworzenia testu obciążeniowego za pomocą **Kreatora nowego testu obciążeniowego**, jest dodawany początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego. Po utworzeniu testu obciążenia, można dodać nowe liczniki do istniejących zestawów liczników za pomocą edytora testu obciążenia.|-   [Porady: Dodawanie liczników do zestawów liczników](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Porady: Dodawanie zbiorów liczników niestandardowych](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Określ reguły progu za pomocą liczników dla testu obciążeniowego:** reguły progu jest regułą, która jest ustawiona na licznik wydajności poszczególnych do monitorowania użycia zasobów systemowych podczas testu obciążeniowego. Definicje zestawu liczników zawiera wstępnie zdefiniowany próg reguły dla wielu kluczowych liczników wydajności. Reguły progów w testach obciążenia porównanie wartości licznika wydajności za pomocą wartości stałej lub inną wartość licznika wydajności.|-   [Porady: Dodawanie reguły progu](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Przypisać przyjazne nazwy komputerów, do których licznik zestawów są mapowane:** można dodać tagów, które umożliwiają łatwą do rozpoznania nazwę na komputerze. Znaczniki są wyświetlane w **mapowaniach zbioru liczników** węzeł dla drzewa w edytorze testu obciążenia. Co ważniejsze, znaczniki są wyświetlane w raportach programu Excel, które pomagają zainteresowanych stron, jaką rolę zidentyfikować komputer ma w teście obciążenia, na przykład, "Server1 sieci Web w lab2" lub "SQL Server2 w pakiecie office Phoenix".<br /><br /> Aby uzyskać więcej informacji, zobacz [testy obciążenia raport wyników dla potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Korzystanie z zestawów liczników

Narzędzia do testów obciążenia, zbieranie i wykres danych wydajności przy użyciu liczników wraz z upływem czasu. Dane licznika są zbierane w odstępach czasu określonych przez użytkownika podczas przebiegu testu obciążeniowego. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Liczniki mogą być wyświetlane w czasie wykonywania, lub można je wyświetlić po testu obciążenia przy użyciu *analizatora testu obciążenia*.

Dane licznika są zbierane na serwerze i na dowolnym komputerze, gdy test jest wykonywany. Jeśli w zestawie komputerów agentów, na którym chcesz uruchomić testy, liczniki są również zbierane na tych komputerach.

Istnieją trzy kategorie liczników: wartości procentowych, liczniki i średnie. Niektóre przykłady to % użycia procesora CPU, liczniki blokady programu SQL Server i usługi IIS żądań na sekundę.

![Zestawy liczników testu obciążeniowego](../test/media/loadtestcountersets.png)

Dane wydajności dotyczące poszczególnych żądań HTTP jest zgłaszany przez komputer, który uruchamia test. na przykład komputer agenta. W przypadku żądań może monitorować dane, takie jak Średni czas do pierwszego bajtu, czas reakcji i żądań na sekundę.

Aby ułatwić zbierania danych wydajności na serwerze sieci web, programu Visual Studio Enterprise zapewnia zbiorów liczników wstępnie zdefiniowanych, nazwanych, oparte na technologii do użycia w testach obciążenia. Te zestawy są przydatne podczas konfigurowania serwera, na którym działa program IIS, ASP.NET lub SQL Server. Liczniki, które nie są dostarczane w domyślny zbiór liczników można dodać za pomocą edytora testu obciążenia. Należy dodać komputerach lub serwerach, w ramach testu do testu obciążenia, aby upewnić się, że można monitorować użycie zasobów na tych komputerach. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie zbiorami liczników](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Analiza wyników przebiegów obciążeniowych często wymaga znajomości specyficznego dla domeny konkretnego obszaru, aby dowiedzieć się, jakie dane, aby zebrać, gdzie należy reguły progów zestawu i jak stwierdzić, gdy miara odzwierciedla konkretnego problemu w aplikacji. Aby uzyskać więcej informacji, zobacz [o reguły progów](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Zagadnienia interwału próbkowania licznika wydajności

Wybierz odpowiednią **częstotliwość próbkowania** uruchomieniowe właściwości w teście obciążenia, na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, np. wartość domyślna pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. Dla dłuższych testów obciążenia zwiększenie częstotliwości próbkowania powoduje zmniejszenie ilości zebranych danych. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Poniżej przedstawiono niektóre wytyczne dotyczące częstotliwości próbkowania.

|Czas trwania testu obciążenia|Częstotliwość próbkowania zalecane|
|-|-----------------------------|
|\< 1 godzina|5 sekund|
|1−8 godzin|15 sekund|
|8−24 godzin|30 sekund|
|> 24 godziny|60 sekund|

## <a name="store-performance-data"></a>Dane dotyczące wydajności Store

Podczas uruchomienia testu obciążenia, dane licznika wydajności są zbierane i przechowywane w *repozytorium wyników testów obciążenia*. Aby uzyskać więcej informacji, zobacz [wyniki testu obciążeniowego Zarządzanie obciążenia test repozytorium wyników](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Reguły progu — informacje

A *regułę progową* jest regułą, która jest ustawiona na licznik wydajności poszczególnych do monitorowania użycia zasobów systemowych podczas testu obciążeniowego. Definicje zestawu liczników zawiera wstępnie zdefiniowany próg reguły dla wielu kluczowych liczników wydajności. Aby uzyskać więcej informacji, zobacz [zestawów liczników użycia, aby pomóc w analizowaniu danych liczników wydajności w testach obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Reguły progów i poziomy

Po utworzeniu reguły progów w testach obciążenia, wybierz między dwoma rodzajami reguły:

Porównanie ze stałą&mdash;porównanie wartości licznika wydajności z wartością stałą.

Porównanie liczników&mdash;porównanie wartości licznika wydajności na inną wartość licznika wydajności.

Podczas tworzenia reguły progów, można również ustawić poziomy dla tej reguły. Poziomy są progu ostrzeżenia i progu krytycznego. Podczas wyświetlania przebiegu testu obciążeniowego naruszenia progu poziomu ostrzeżenia są wskazywane przez żółty symboli i naruszenia progu krytycznego poziomu są wskazywane przez czerwony symbol.

## <a name="the-alert-if-over-property"></a>Właściwości alertu, gdy nastąpi przekroczenie

Ustaw **alertu, gdy nastąpi przekroczenie** właściwości **True** do wskazania przekroczenia progu to problem. Na przykład, jeśli ustawiono regułę progową w **czas procesora (%)**, a użytkownik chce otrzymywać alerty, jeśli wartość jest większa niż 90, użyj **Porównaj stałą** typ reguły, ustaw **próg krytyczny Wartość** do 90, a następnie ustaw **alertu, gdy nastąpi przekroczenie** do **True**.

Ustaw **alertu, gdy nastąpi przekroczenie** właściwości **False** do wskazywania objętych poniżej wartości progowej problem. Na przykład, jeśli ustawiono regułę progową w **żądań na sekundę**, a użytkownik chce otrzymywać alerty, jeśli wartość jest poniżej 50, użyj **Porównaj stałą** typ reguły, ustaw **krytyczną wartość progową** do 50, a następnie ustaw **alertu, gdy nastąpi przekroczenie** do **False**.

## <a name="see-also"></a>Zobacz także

- [Porady: Dodawanie reguły progu](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analizowanie naruszeń zasady progu](../test/analyze-threshold-rule-violations-in-load-tests.md)