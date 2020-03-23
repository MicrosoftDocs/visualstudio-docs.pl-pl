---
title: Widok szczegółów funkcji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6e5bd33d9924784220addafca85a63f550df02c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779262"
---
# <a name="function-details-view"></a>Widok szczegółów funkcji
W oknie **Widok szczegółów funkcji** wyświetlane są następujące informacje:

- Wykres słupkowy **rozkładu kosztów** reprezentuje relacje między wybraną funkcją a funkcjami wywołującymi, które wykonały wybraną funkcję, oraz między wybraną funkcją a wywoływanymi przez nią funkcjami.

- Tabela **Szczegóły wydajności funkcji,** w której są wyświetlane dane profilowania podsumowania dla określonej funkcji.

- Okno **Widok kodu funkcji,** który pokazuje kod funkcji, gdy kod jest dostępny.

  Okno **Widok kodu funkcji** jest osobnym okienkiem. Domyślnie dwa okienka są dzielone w poziomie, a okno **Widok kodu funkcji** jest umieszczone w dolnej części ramki.

- Aby podzielić dwa okienka w pionie, kliknij pozycję **Podzielony ekran w pionie** na pasku narzędzi.

- Aby zmienić względny rozmiar okienek, kliknij zacieniowane obramowanie między ramkami i przeciągnij obramowanie w inne miejsce.

## <a name="cost-distribution-bar-chart"></a>Wykres słupkowy rozkładu kosztów

### <a name="performance-metrics"></a>Metryki wydajności
 Na liście rozwijanej **Metryka Wydajność** można określić, które wartości są wyświetlane w widoku. Wartości, które są dostępne zależą od metody profilowania, która została użyta w pliku danych profilowania. Nazwy w nawiasach są nazwami wierszy w tabeli **Szczegóły wydajności funkcji.**

### <a name="bar-chart"></a>Wykres słupkowy
 **Funkcje wywołujące**

 Pasek **funkcji wywołujących** pokazuje funkcje, które wywoływane są dla wybranej funkcji. Rozmiar bloku, który zawiera funkcję wywołującą jest proporcjonalna do udziału funkcji wywołującej do całkowitej wartości metryki wydajności dla wybranej funkcji.

 Można kliknąć nazwę funkcji wywołującej, aby uczynić ją wybraną funkcją w widoku.

- Jeśli istnieje zbyt wiele funkcji wywołujących do listy, funkcje z najmniejszych składek są zbierane w **bloku Inne.** Kliknij **pozycję Inne,** aby wyświetlić wszystkie funkcje połączeń i wywoływane wybranej funkcji w oknie **Widok wywołujący/wywoływany.** Aby uzyskać więcej informacji, zobacz [Widok wywołującego/wywoływania](../profiling/caller-callee-view.md).

- Jeśli nie ma żadnych funkcji wywołujących lub jeśli funkcja jest funkcją wprowadzania wątku lub procesu, pojawi się **górny** stos bloku.

  **Wybrana funkcja**

  Wybrany pasek funkcji pokazuje wkład wywoływanych funkcji i kodu w wybranej funkcji do metryki całkowitej wydajności wybranej funkcji. Rozmiar bloku, który zawiera wywołaną funkcję lub treść funkcji jest proporcjonalny do jego udziału w całkowitej wartości metryki wydajności dla wybranej funkcji.

  Można kliknąć nazwę wywoływanej funkcji, aby uczynić ją wybraną funkcją w widoku.

- **Całkowita** wartość jest metryką wydajności dla wybranej funkcji.

- **Treść funkcji** bloku reprezentuje kwotę całkowitej wartości metryki wydajności, które wystąpiły w bezpośrednim wykonaniu kodu w treści funkcji.

- Funkcje wywoływane przez wybraną funkcję są wyświetlane w blokach. Rozmiar wybranego bloku funkcji reprezentuje ilość metryki całkowitej wydajności dla wybranej funkcji, która wystąpiła w wywoływanej funkcji.

- Jeśli istnieje zbyt wiele funkcji wywołujących do listy, funkcje z najmniejszych składek są zbierane w **bloku Inne.** Kliknij **pozycję Inne,** aby wyświetlić wszystkie funkcje połączeń i wywoływane wybranej funkcji w oknie **Widok wywołujący/wywoływany.** Aby uzyskać więcej informacji, zobacz [Widok wywołującego/wywoływania](../profiling/caller-callee-view.md).

- Jeśli nie ma żadnych wywoływanych funkcji, zostanie wyświetlony blok **Dolny stos.**

## <a name="function-performance-details"></a>Szczegóły wydajności funkcji
 Tabela Szczegóły wydajności funkcji zawiera dane podsumowujące dla metryk wydajności wybranej funkcji. Pojawi się zarówno wartość, jak i wartość procentowa. Należy określić dane profilowania, które pojawiają się na wykresie i tabelę szczegółów na liście **Metryki Wydajność.**

|Kolumna|Opis|
|------------|-----------------|
|**Wyłączne**|- Ilość metryki wydajności, które wystąpiły podczas wykonywania treści funkcji.|
|**W połączeniach**|- Ilość metryki wydajności, która wystąpiła w funkcjach wywoływanych przez wybraną funkcję.|
|**Razem włącznie**|- Suma wartości **Exclusive** i **In Calls.**|

## <a name="function-code-view"></a>Widok kodu funkcji
 Okno **Widok kodu funkcji** wyświetla listę kodu źródłowego, gdy jest on dostępny. Obok wierszy kodu źródłowego, które wywołują inne funkcje, zacieniowana kolumna zawiera wartości metryki wydajności dla wywoływaną funkcję. Aby edytować kod źródłowy, kliknij łącze do pliku kodu źródłowego.

## <a name="cost-distribution-bar-chart-values"></a>Wartości wykresu słupkowego rozkładu kosztów

### <a name="sampling"></a>Próbkowanie
 W poniższej tabeli wyjaśniono wartości na liście Metryki wydajności dla profilowania danych, które zostały zebrane przy użyciu metody próbkowania.

|||
|-|-|
|**Próbki włączające (pobrane próbki)**|- Dla funkcji wywołującej liczba próbek, które zostały zebrane, gdy wybrana funkcja została wywołana przez tę funkcję wywołującą.<br />- Dla treści funkcji liczba próbek, które zostały zebrane podczas wykonywania przez wybraną funkcję własnego kodu.<br />- Dla wywoływanej funkcji liczba próbek, które zostały zebrane podczas wykonywania wywoływanej funkcji z powodu wywołania z wybranej funkcji.|

### <a name="instrumentation"></a>Oprzyrządowanie
 W poniższej tabeli wyjaśniono wartości na liście Metryki wydajności dla profilowania danych, które zostały zebrane przy użyciu metody instrumentacji.

|||
|-|-|
|**Czas włącznie, który upłynął (czas, który upłynął)**|Czas, który upłynął, obejmuje czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br /><br /> - Dla **funkcji wywołującej**, ilość czasu, który upłynął na wykonywanie wystąpień wybranej funkcji, które zostały wywołane przez funkcję. Uwzględniono czas spędzony w funkcjach wywoływanych przez wybraną funkcję.<br />- Dla **treści funkcji**, całkowita ilość czasu spędzonego na wykonywaniu kodu wybranej funkcji. Czas spędzony w wywoływanych funkcjach nie jest uwzględniony.<br />- Dla funkcji o nazwie, czas spędzony na wykonywaniu wystąpień funkcji, które zostały wywołane przez wybraną funkcję. Suma obejmuje czas spędzony w funkcjach wywoływanych przez funkcję. Uwzględniono czas spędzony w funkcjach wywoływanych przez wybraną funkcję.|
|**Czas włącznie aplikacji (czas aplikacji)**|Czas aplikacji nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br /><br /> - Dla **funkcji wywołującej**, ilość czasu aplikacji, który został spędzony na wykonywaniu wystąpień wybranej funkcji, które zostały wywołane przez funkcję. Uwzględniono czas spędzony w funkcjach wywoływanych przez wybraną funkcję.<br />- Dla **treści funkcji**, całkowita ilość czasu aplikacji spędzonego na wykonywaniu kodu wybranej funkcji. Czas spędzony w wywoływanych funkcjach nie jest uwzględniony.<br />- Dla wywoływanej funkcji ilość czasu aplikacji spędzonego na wykonywaniu wystąpień funkcji, które zostały wywołane przez wybraną funkcję. Suma obejmuje czas spędzony w funkcjach wywoływanych przez funkcję.|

### <a name="net-memory"></a>Pamięć .NET
 W poniższej tabeli wyjaśniono wartości na liście Metryki wydajności dla profilowania danych, które zostały zebrane przy użyciu metody profilowania pamięci .NET.

|||
|-|-|
|**Alokacje włącznie (alokacje)**|- Dla **funkcji wywołującej**, liczba obiektów, które zostały przydzielone przez wystąpienia wybranej funkcji, że funkcja wywołana. Liczba ta zawiera obiekty, które zostały przydzielone przez funkcje wywoływane przez wybraną funkcję.<br />- Dla **treści funkcji**, liczba obiektów, które zostały przydzielone przez wybraną funkcję podczas wykonywania własnego kodu. Obiekty przydzielone w funkcjach wywoływanych przez wybraną funkcję nie są uwzględniane.<br />- Dla wywoływanej funkcji liczba obiektów, które zostały przydzielone przez wystąpienia funkcji, które zostały wywołane przez wybraną funkcję. Liczba zawiera obiekty, które zostały przydzielone przez funkcje, które funkcja wywoływana.|
|**Bajty włącznie (bajty)**|- Dla **funkcji wywołującej**, liczba bajtów, które zostały przydzielone przez wystąpienia wybranej funkcji, że funkcja wywołana. Liczba ta zawiera bajty, które zostały przydzielone przez funkcje wywoływane przez wybraną funkcję.<br />- Dla **treści funkcji**całkowita liczba bajtów, które zostały przydzielone przez wybraną funkcję podczas wykonywania własnego kodu. Bajty przydzielone w funkcjach wywoływanych przez wybraną funkcję nie są uwzględniane.<br />- Dla wywoływanej funkcji liczba bajtów, które zostały przydzielone przez wystąpienia funkcji, które zostały wywołane przez wybraną funkcję. Liczba zawiera bajty, które zostały przydzielone przez funkcje, które wywoływała funkcja.|

### <a name="concurrency"></a>Współbieżność
 W poniższej tabeli wyjaśniono wartości na liście Metryki wydajności dla profilowania danych, które zostały zebrane przy użyciu metody współbieżności.

|||
|-|-|
|**Rywalizacje włączające (rywalizacje)**|- Dla **funkcji wywołującej**, liczba zdarzeń rywalizacji o zasoby, które wystąpiły w wystąpieniach wybranej funkcji, którą wywoływała funkcja. Liczba zawiera zdarzenia rywalizacji w funkcjach wywoływanych przez wybraną funkcję.<br />- Dla **treści funkcji**, całkowita liczba zdarzeń rywalizacji, które wystąpiły podczas wykonywania przez funkcję własnego kodu. Rywalizacje występujące w funkcjach, które zostały wywołane przez wybraną funkcję, nie są uwzględniane.<br />- Dla wywoływanej funkcji liczba zdarzeń rywalizacji, które wystąpiły w wystąpieniach funkcji, które zostały wywołane przez wybraną funkcję. Liczba zawiera zdarzenia rywalizacji, które wystąpiły w funkcjach wywoływanych przez funkcję.|
|**Włącznie zablokowany czas (czas zablokowany)**|- Dla funkcji wywołującej czas spędzony w zdarzeniach rywalizacji o zasoby dla wystąpień wybranej funkcji, którą wywoływała funkcja. Czas obejmuje zablokowany czas w funkcjach wywoływanych przez wybraną funkcję.<br />- Dla **treści funkcji**, całkowity czas spędzony w zdarzeniach rywalizacji, które wystąpiły podczas wykonywania przez funkcję własnego kodu. Rywalizacje występujące w funkcjach, które wywoływana jest wybrana funkcja, nie są uwzględniane.<br />- Dla wywoływanej funkcji czas spędzony w zdarzeniach rywalizacji o zasoby dla wystąpień funkcji, którą wywoływała wybrana funkcja. Czas obejmuje zablokowany czas, który wystąpił w funkcjach wywoływanych przez funkcję.|
