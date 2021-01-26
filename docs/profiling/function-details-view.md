---
title: Widok szczegółów funkcji | Microsoft Docs
description: W Eksplorator wydajności zapoznaj się z oknem widok szczegółów funkcji, wykresem słupkowym dystrybucji kosztów, tabelą szczegóły wydajności funkcji i oknem widok kodu funkcji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6e812f0fdef46d0ac5ef42788c2f854922a7375c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801263"
---
# <a name="function-details-view"></a>Widok szczegółów funkcji
W oknie **Widok szczegółów funkcji** są wyświetlane następujące informacje:

- Wykres słupkowy **dystrybucji kosztów** reprezentuje relacje między funkcją, którą wybierzesz, a funkcjami wywołującymi, które wykonali wybraną funkcję, oraz między wybraną funkcją i funkcjami, które zostały wywołane przez nią.

- Tabela **szczegóły wydajności funkcji** , która zawiera podsumowanie danych profilowania dla określonej funkcji.

- Okno **widoku Kod funkcji** , w którym jest wyświetlany kod funkcji, gdy kod jest dostępny.

  Okno **Widok kodu funkcji** jest osobnym okienkiem. Domyślnie dwa okienka są podzielone w poziomie, a okno **Widok kodu funkcji** jest umieszczane u dołu ramki.

- Aby podzielić dwa okienka w pionie, kliknij przycisk **Podziel ekran w pionie** na pasku narzędzi.

- Aby zmienić względny rozmiar okienek, kliknij zacienione obramowanie między ramkami i przeciągnij obramowanie do innej lokalizacji.

## <a name="cost-distribution-bar-chart"></a>Wykres słupkowy dystrybucji kosztów

### <a name="performance-metrics"></a>Metryki wydajności
 Z listy rozwijanej **Metryka wydajności** możesz określić, które wartości są wyświetlane w widoku. Dostępne wartości zależą od metody profilowania, która została użyta w pliku danych profilowania. Nazwy w nawiasach są nazwami wierszy w tabeli **szczegóły wydajności funkcji** .

### <a name="bar-chart"></a>Wykres słupkowy
 **Wywoływanie funkcji**

 Na pasku **funkcje wywołujące** są wyświetlane funkcje, które wywołały wybraną funkcję. Rozmiar bloku, który zawiera funkcję wywołującą, jest proporcjonalny do udziału funkcji wywołującej do łącznej wartości metryki wydajności dla wybranej funkcji.

 Możesz kliknąć nazwę funkcji wywołującej, aby wybrać ją jako funkcję w widoku.

- Jeśli istnieje zbyt wiele funkcji wywołujących do listy, funkcje o najmniejszej liczbie udziałów są zbierane w **innym** bloku. Kliknięcie przycisku **inne** umożliwia wyświetlenie wszystkich wywoływanych i wywoływanych funkcji wybranej funkcji w oknie **Widok wywołujący/wywoływany** . Aby uzyskać więcej informacji, zobacz [Widok wywołujący/wywoływany](../profiling/caller-callee-view.md).

- Jeśli nie ma żadnych funkcji wywołujących lub jeśli funkcja jest funkcją wejścia wątku lub procesu, pojawia się **Górna część bloku stosu** .

  **Wybrana funkcja**

  Wybrany pasek funkcji przedstawia wkłady wywołanych funkcji i kodu w wybranej funkcji do całkowitej metryki wydajności wybranej funkcji. Rozmiar bloku, który zawiera wywołaną funkcję lub treść funkcji, jest proporcjonalny do jego udziału w łącznej wartości metryki wydajności dla wybranej funkcji.

  Możesz kliknąć nazwę wywoływanej funkcji, aby wybrać ją jako funkcję w widoku.

- Wartość **całkowita** jest metryką wydajności dla wybranej funkcji.

- Blok **treści funkcji** reprezentuje ilość łącznej wartości metryki wydajności, która wystąpiła w bezpośrednim wykonaniu kodu w treści funkcji.

- Funkcje, które są wywoływane przez wybraną funkcję, są wymienione w bloku. Rozmiar bloku wybrane funkcje reprezentuje ilość całkowitej metryki wydajności dla wybranej funkcji, która wystąpiła w wywołanej funkcji.

- Jeśli istnieje zbyt wiele funkcji wywołujących do listy, funkcje o najmniejszej liczbie udziałów są zbierane w **innym** bloku. Kliknięcie przycisku **inne** umożliwia wyświetlenie wszystkich wywoływanych i wywoływanych funkcji wybranej funkcji w oknie **Widok wywołujący/wywoływany** . Aby uzyskać więcej informacji, zobacz [Widok wywołujący/wywoływany](../profiling/caller-callee-view.md).

- Jeśli nie ma żadnych funkcji, zostanie wyświetlony **dolny blok stosu** .

## <a name="function-performance-details"></a>Szczegóły wydajności funkcji
 Tabela szczegóły wydajności funkcji zawiera dane podsumowania metryk wydajności wybranej funkcji. Zostanie wyświetlona wartość i procent. Określ dane profilowania, które pojawiają się na wykresie i tabeli szczegółów na liście **metryki wydajności** .

|Kolumna|Opis|
|------------|-----------------|
|**Klucz**|— Ilość metryki wydajności, która wystąpiła w trakcie wykonywania treści funkcji.|
|**W wywołaniach**|— Ilość metryki wydajności, która wystąpiła w funkcjach wywołanych przez wybraną funkcję.|
|**Łącznie włącznie**|— Suma wartości **wyłącznych** i **w ramach wywołań** .|

## <a name="function-code-view"></a>Widok kodu funkcji
 W oknie **Widok kodu funkcji** zostanie wyświetlona lista kodu źródłowego, gdy jest on dostępny. Obok wierszy kodu źródłowego, które wywołują inne funkcje, zacieniowana kolumna zawiera wartości metryk wydajności dla wywołanej funkcji. Aby edytować kod źródłowy, kliknij link do pliku kodu źródłowego.

## <a name="cost-distribution-bar-chart-values"></a>Wartości wykresu słupkowego dystrybucji kosztów

### <a name="sampling"></a>Próbkowanie
 W poniższej tabeli objaśniono wartości z listy metryk wydajności dla danych profilowania zbieranych przy użyciu metody próbkowania.

|Wartość|Opis|
|-|-|
|**Próbki włączne (zebrane próbki)**|— Dla funkcji wywołującej liczba próbek zebranych, gdy wybrana funkcja została wywołana przez tę funkcję wywołującą.<br />-Dla treści funkcji, liczba próbek zebranych, gdy wybrana funkcja wykonywała własny kod.<br />-Dla wywoływanej funkcji, liczba próbek zebranych podczas wykonywania wywołanej funkcji z powodu wywołania z wybranej funkcji.|

### <a name="instrumentation"></a>Oprzyrządowanie
 W poniższej tabeli objaśniono wartości z listy metryk wydajności dla danych profilowania zebranych za pomocą metody instrumentacji.

|Wartość|Opis|
|-|-|
|**Czas włączny, który upłynął (czas, który upłynął)**|Czas, który upłynął, obejmuje czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br /><br /> — Dla **funkcji wywołującej**, ilość czasu, który zajęło wykonywanie wystąpień wybranej funkcji, które zostały wywołane przez funkcję. Zostanie uwzględniony czas spędzony na funkcjach wywoływanych przez wybraną funkcję.<br />— Dla **treści funkcji**— łączną ilość czasu spędzonego na wykonywaniu kodu wybranej funkcji. Czas spędzony na wywołanych funkcjach nie jest uwzględniony.<br />-Dla wywoływanej funkcji, ilość czasu poświęcanego na wykonywanie wystąpień funkcji, które zostały wywołane przez wybraną funkcję. Łącznie obejmuje czas spędzony w funkcjach wywołanych przez funkcję. Zostanie uwzględniony czas spędzony na funkcjach wywoływanych przez wybraną funkcję.|
|**Czas włączny aplikacji (czas aplikacji)**|Czas aplikacji nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br /><br /> — Dla **funkcji wywołującej**, ilość czasu aplikacji, która zajęła wykonywanie wystąpień wybranej funkcji, które zostały wywołane przez funkcję. Zostanie uwzględniony czas spędzony na funkcjach wywoływanych przez wybraną funkcję.<br />-Dla **treści funkcji**, łączną ilość czasu aplikacji poświęcanego na wykonanie kodu wybranej funkcji. Czas spędzony na wywołanych funkcjach nie jest uwzględniony.<br />-Dla wywoływanej funkcji, czas aplikacji poświęcany na wykonywanie wystąpień funkcji, które zostały wywołane przez wybraną funkcję. Łącznie obejmuje czas spędzony w funkcjach wywołanych przez funkcję.|

### <a name="net-memory"></a>Pamięć platformy .NET
 W poniższej tabeli objaśniono wartości z listy metryk wydajności dla danych profilowania zbieranych przy użyciu metody profilowania pamięci platformy .NET.

|Wartość|Opis|
|-|-|
|**Przydziały włączne (przydziały)**|— Dla **funkcji wywołującej** liczba obiektów przydzielonej przez wystąpienia wybranej funkcji, która została wywołana przez funkcję. Liczba zawiera obiekty, które zostały przydzielone przez funkcje wywoływane przez wybraną funkcję.<br />— Dla **treści funkcji**, liczby obiektów, które zostały przydzielone przez wybraną funkcję, gdy wykonywał własny kod. Obiekty przydzielone w funkcjach wywoływanych przez wybraną funkcję nie są uwzględniane.<br />-Dla wywoływanej funkcji, liczba obiektów przydzielono przez wystąpienia funkcji, które zostały wywołane przez wybraną funkcję. Liczba zawiera obiekty, które zostały przydzielone przez funkcje wywoływane przez funkcję.|
|**Bajty włącznie (w bajtach)**|— Dla **funkcji wywołującej** liczba bajtów, które zostały przydzielone przez wystąpienia wybranej funkcji, wywołane przez funkcję. Liczba zawiera bajty, które zostały przydzielone przez funkcje wywoływane przez wybraną funkcję.<br />— Dla **treści funkcji**— całkowita liczba bajtów, które zostały przydzielone przez wybraną funkcję podczas wykonywania własnego kodu. Bajty przydzielone w funkcjach wywoływanych przez wybraną funkcję nie są uwzględniane.<br />-Dla wywoływanej funkcji, liczba bajtów, które zostały przydzielone przez wystąpienia funkcji, które zostały wywołane przez wybraną funkcję. Liczba zawiera bajty, które zostały przydzielone przez funkcje wywoływane przez funkcję.|

### <a name="concurrency"></a>Współbieżność
 W poniższej tabeli objaśniono wartości z listy metryk wydajności dla danych profilowania zbieranych przy użyciu metody współbieżności.

|Wartość|Opis|
|-|-|
|**Rywalizacje włączne (rywalizacje)**|-Dla **funkcji wywołującej** liczba zdarzeń rywalizacji o zasoby, które wystąpiły w wystąpieniach wybranej funkcji wywołanej przez funkcję. Liczba zawiera zdarzenia rywalizacji w funkcjach wywoływanych przez wybraną funkcję.<br />— Dla **treści funkcji**— całkowita liczba zdarzeń rywalizacji, które wystąpiły podczas wykonywania przez funkcję własnego kodu. Rywalizacje występujące w funkcjach, które zostały wywołane przez wybraną funkcję, nie są uwzględniane.<br />-Dla wywoływanej funkcji, liczba zdarzeń rywalizacji, które wystąpiły w wystąpieniach funkcji, które zostały wywołane przez wybraną funkcję. Liczba zawiera zdarzenia rywalizacji, które wystąpiły w funkcjach wywołanych przez funkcję.|
|**Włączny czas blokowania (czas blokowania)**|— Dla funkcji wywołującej czas spędzony w zdarzeniach rywalizacji o zasoby dla wystąpień wybranej funkcji, która została wywołana. Czas obejmuje czas blokowania w funkcjach, które zostały wywołane przez wybraną funkcję.<br />-Dla **treści funkcji**, łączny czas spędzony w zdarzeniach rywalizacji, które wystąpiły podczas wykonywania własnego kodu przez funkcję. Rywalizacje występujące w funkcjach wywoływanych przez wybraną funkcję nie są uwzględniane.<br />-Dla wywoływanej funkcji, czas spędzony w zdarzeniach rywalizacji o zasoby dla wystąpień funkcji, która została wywołana przez wybraną funkcję. Czas obejmuje czas blokowania, który wystąpił w funkcjach wywołanych przez funkcję.|
