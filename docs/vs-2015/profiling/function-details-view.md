---
title: Widok szczegółów funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6f2246cfe9eb2ae9ae6641ca316db440f153f92
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799594"
---
# <a name="function-details-view"></a>Widok szczegółów funkcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Widok szczegółów funkcji** wyświetlane są następujące informacje:  
  
- **Dystrybucji** wykres słupkowy przedstawia relacje między wybranej funkcji i funkcji wywołujących wykonanych wybranej funkcji oraz między wybranej funkcji i funkcji, które zostały wywołane przez go.  
  
- **Szczegóły wydajności funkcji** tabelę, która pokazuje, podsumowania danych profilowania dla funkcji, które określisz.  
  
- **Widok kodu funkcji** okno, które zawiera kod funkcji, jeśli kod jest dostępny.  
  
  **Widok kodu funkcji** okno jest oddzielne okienko. Domyślnie dwa okienka są dzielone w poziomie, a **widok kodu funkcji** okna znajduje się w dolnej części ramki.  
  
- Aby podzielić dwa okienka w pionie, kliknij **Podziel ekran w pionie** na pasku narzędzi.  
  
- Aby zmienić względną wielkość paneli, kliknij zacieniony obramowanie klatek, a następnie przeciągnij krawędź do innej lokalizacji.  
  
## <a name="cost-distribution-bar-chart"></a>Wykres słupkowy dystrybucji kosztów  
  
### <a name="performance-metrics"></a>Metryki wydajności  
 W **Metryka wydajności** listy rozwijanej, można określić wartości, które są wyświetlane w widoku. Wartości, które są dostępne, zależą od metody profilowania, który był używany w pliku danych profilowania. Nazwy w nawiasach są nazwami wierszy w **szczegóły wydajności funkcji** tabeli.  
  
### <a name="bar-chart"></a>Wykres słupkowy  
 **Wywoływanie funkcji**  
  
 **Podczas wywoływania funkcji** pasek pokazuje funkcje, które wywoływały wybranej funkcji. Rozmiar bloku, który zawiera funkcji wywołującej jest proporcjonalna do udziału funkcji wywołującej na wartość całkowitą metryki wydajności dla wybranej funkcji.  
  
 Możesz kliknąć nazwę funkcji wywołującej, aby stał się wybranej funkcji w widoku.  
  
- W przypadku zbyt wielu funkcji wywołujących, aby wyświetlić listę funkcji z najmniejszą wkładów są gromadzone w **innych** bloku. Kliknij przycisk **innych** do wyświetlenia wszystkich funkcji wywołujących i wywoływanych wybranych funkcji w **widok wywołujący/wywoływany** okna. Aby uzyskać więcej informacji, zobacz [widok wywołujący/wywoływany](../profiling/caller-callee-view.md).  
  
- Jeśli brak wywołania funkcji lub jeśli funkcja jest funkcją wpis w wątku lub procesu, **górze stosu** pojawi się blok.  
  
  **Wybranej funkcji**  
  
  Pasek wybranej funkcji pokazuje wkład wywoływane funkcje i kodu w wybranej funkcji na metryki wydajności całkowitej z wybranej funkcji. Rozmiar bloku, który zawiera funkcję o nazwie lub treści funkcji jest proporcjonalnie swój wkład zgodnie z wartością całkowitą metryki wydajności dla wybranej funkcji.  
  
  Możesz kliknąć nazwę wywoływanej funkcji, aby wybranej funkcji w widoku.  
  
- **Całkowita** wartość metryki wydajności dla wybranej funkcji.  
  
- **Treści funkcji** reprezentuje blok kwota łączna wartość metryki wydajności, który wystąpił w bezpośrednie wykonywanie kodu w treści funkcji.  
  
- Funkcje, które są wywoływane przez wybraną funkcję są wyświetlane w blokach. Rozmiar bloku funkcji reprezentuje ilość metryki wydajności całkowitej wybranej funkcji, które wystąpiły w wywołanej funkcja.  
  
- W przypadku zbyt wielu funkcji wywołujących, aby wyświetlić listę funkcji z najmniejszą wkładów są gromadzone w **innych** bloku. Kliknij przycisk **innych** do wyświetlenia wszystkich funkcji wywołujących i wywoływanych wybranych funkcji w **widok wywołujący/wywoływany** okna. Aby uzyskać więcej informacji, zobacz [widok wywołujący/wywoływany](../profiling/caller-callee-view.md).  
  
- Jeśli nie wywoływane funkcje **dół stosu** pojawi się blok.  
  
## <a name="function-performance-details"></a>Szczegóły wydajności — funkcja  
 Tabela Szczegóły wydajności funkcji zawiera podsumowania danych dla metryki wydajności wybranej funkcji. Są wyświetlane zarówno wartość, jak i wartość procentowa. Określ Określ tabelę danych profilowania, których są wyświetlane na wykresie i szczegóły **Metryka wydajności** listy.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączne**|-Ilość metryki wydajności, który wystąpił podczas wykonywania treści funkcji.|  
|**W wywołaniach**|-Ilość metryki wydajności, który wystąpił w funkcje, które wywołały wybranej funkcji.|  
|**Całkowita (włącznie)**|— W sumie **wyłączne** i **wywołań w** wartości.|  
  
## <a name="function-code-view"></a>Widok kodu funkcji  
 **Widok kodu funkcji** okna wyświetla listę kodu źródłowego, gdy będzie ona dostępna. Obok wierszy kodu źródłowego, które wywołują innych funkcji cieniowanych kolumna zawiera wartości metryk wydajności dla wywołanej funkcji. Aby zmodyfikować kod źródłowy, kliknij link do pliku kodu źródłowego.  
  
## <a name="cost-distribution-bar-chart-values"></a>Koszt dystrybucji pasek wartości wykresu  
  
### <a name="sampling"></a>Próbkowania  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, które zostały zebrane przy użyciu metody próbkowania.  
  
|||  
|-|-|  
|**Próbki włączne (zebranych próbek)**|— Aby wywołanie funkcji, liczba próbek, które zostały zebrane, gdy wybrane funkcja została wywołana przez tę funkcję wywołania.<br />— Aby treść funkcji — liczba próbek, które zostały zebrane podczas wykonywania swój własny kod wybranej funkcji.<br />– W przypadku funkcji, liczba próbek, które zostały zebrane podczas wykonywania wywołanej funkcji ze względu na wywołania z wybranej funkcji.|  
  
### <a name="instrumentation"></a>Oprzyrządowanie  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, które zostały zebrane przy użyciu metody instrumentacji.  
  
|||  
|-|-|  
|**Czas Włączny, który upłynął (czas)**|Czas trwania obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br /><br /> -Aby **podczas wywoływania funkcji**, ilość minionego czasu, jaki był poświęcony na wykonywanie wystąpienia wybranej funkcji, które zostały wywołane przez funkcję. Czas w funkcjach wywoływanych przez wybranej funkcji jest dołączony.<br />-Aby **treści funkcji**, całkowita ilość czasu poświęconego na wykonywanie kodu z wybranej funkcji. Czas potrzebny do funkcji o nazwie nie jest włączony.<br />– W przypadku wywołana funkcja kwota czas wykonywania wystąpienia funkcji, które były wywoływane przez wybraną funkcję. Łączna liczba obejmuje czas spędzony w funkcje, które wywołały funkcję. Czas w funkcjach wywoływanych przez wybranej funkcji jest dołączony.|  
|**Całkowity czas aplikacji (aplikacji czas)**|Czas aplikacji nie obejmuje czas spędzony w wywołaniach do systemu operacyjnego, takie jak przełączeń kontekstu i operacji wejścia/wyjścia.<br /><br /> -Aby **podczas wywoływania funkcji**, czas aplikacji, który był poświęcony na wykonywanie wystąpienia wybranej funkcji, które zostały wywołane przez funkcję. Czas w funkcjach wywoływanych przez wybranej funkcji jest dołączony.<br />-Aby **treści funkcji**, całkowita ilość czasu aplikacji poświęcony na wykonywanie kodu z wybranej funkcji. Czas potrzebny do funkcji o nazwie nie jest włączony.<br />– W przypadku wywołana funkcja kwota aplikacji czas wykonywania wystąpienia funkcji, które były wywoływane przez wybraną funkcję. Łączna liczba obejmuje czas spędzony w funkcje, które wywołały funkcję.|  
  
### <a name="net-memory"></a>Pamięć .NET  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, które zostały zebrane przy użyciu metody profilowania pamięci platformy .NET.  
  
|||  
|-|-|  
|**Przydziały włączne (przydziały)**|-Aby **podczas wywoływania funkcji**, liczbę obiektów, które zostały przydzielone przez wystąpienia wybranej funkcji, która wywołuje funkcję. Liczba uwzględnia obiektów, które zostały przydzielone przez funkcje, które wywołały wybranej funkcji.<br />-Aby **treści funkcji**, liczbę obiektów, które zostały przydzielone przez wybraną funkcję podczas jego wykonywania swój własny kod. Obiekty przydzielone w funkcjach wywoływanych przez wybraną funkcję nie są uwzględniane.<br />– W przypadku funkcji, liczbę obiektów, które zostały przydzielone wystąpień funkcji, które zostały wywołane przez wybraną funkcję. Liczba uwzględnia obiektów, które zostały przydzielone przez funkcje, które wywołały funkcję.|  
|**Bajty włączne (w bajtach)**|-Aby **podczas wywoływania funkcji**, liczba bajtów przydzielonych przez wystąpienia wybranej funkcji, która wywołuje funkcję. Liczba uwzględnia bajtów przydzielonych przez funkcje, które wywołały wybranej funkcji.<br />-Aby **treści funkcji**, całkowita liczba bajtów przydzielonych przez wybraną funkcję, podczas jego wykonywania swój własny kod. Liczby bajtów przydzielonych w funkcjach wywoływanych przez wybraną funkcję nie są uwzględniane.<br />– W przypadku funkcji, liczba bajtów przydzielonych przez wystąpień funkcji, które zostały wywołane przez wybraną funkcję. Liczba uwzględnia bajtów przydzielonych przez funkcje, które wywołały funkcję.|  
  
### <a name="concurrency"></a>Współbieżność  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, które zostały zebrane za pomocą metody współbieżności.  
  
|||  
|-|-|  
|**Rywalizacje włączne (rywalizacji)**|-Aby **podczas wywoływania funkcji**, liczbę zdarzeń rywalizacji zasobów, które wystąpiły w wystąpieniach wybranej funkcji, która wywołuje funkcję. Liczba uwzględnia zdarzenia rywalizacji w funkcje, które wywołały wybranej funkcji.<br />-Aby **treści funkcji**, łączna liczba zdarzeń rywalizacji o zasoby, które wystąpiły podczas wykonywania funkcji swój własny kod. Nie uwzględniono rywalizacji mających miejsce w funkcjach, które były wywoływane przez wybraną funkcję.<br />– W przypadku funkcji, liczbę zdarzeń rywalizacji o zasoby, które wystąpiły w wystąpieniach funkcji, które były wywoływane przez wybraną funkcję. Liczba uwzględnia zdarzenia rywalizacji o zasoby, które wystąpiły w funkcje, które wywołały funkcję.|  
|**Całkowity czas (czas blokowania) blokowania**|– W przypadku funkcji wywołującej czas spędzony w zasobie rywalizacji zdarzenia dla wystąpienia elementu wybranego wywołania funkcji, funkcja wywoływana. Czas obejmuje czas blokowania w funkcjach, które wybrano funkcję o nazwie.<br />-Aby **treści funkcji**, całkowity czas spędzony w zdarzeniach rywalizacji o zasoby, które wystąpiły podczas wykonywania funkcji swój własny kod. Nie uwzględniono rywalizacji mających miejsce w funkcje, które wywołały wybranej funkcji.<br />– W przypadku funkcji, czas spędzony w zdarzeniach rywalizacji o zasób dla wystąpień funkcji, która wywołała wybranej funkcji. Czas obejmuje czas blokowania, który wystąpił w funkcje, które wywołały funkcję.|



