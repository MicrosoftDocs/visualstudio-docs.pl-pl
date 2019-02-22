---
title: Analizowanie użycia procesora CPU | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbbad30fca5dd3ffbaa09c270f6a0b0400d9ea22
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640795"
---
# <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora CPU

Dobrym sposobem, aby rozpocząć badanie problemów z wydajnością w aplikacji jest zrozumieć jego użycie procesora CPU. **Użycie procesora CPU** narzędzie wydajność pokazuje czas procesora CPU i procent poświęcony na wykonywanie kodu w języku C++, C#/Visual Basic i aplikacji JavaScript.

**Użycie procesora CPU** narzędzie można uruchomić w otwartym projekcie programu Visual Studio, zainstalowanych aplikacji Microsoft Store, lub dołączony do uruchomionej aplikacji lub procesu. Narzędzie można uruchomić na maszynach lokalnych lub zdalnych lub na symulatorze lub w emulatorze. Aby uzyskać więcej informacji, zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Możesz uruchomić **użycie procesora CPU** narzędzia z lub bez debugowania. W debugerze można włączyć i wyłączyć profilowania procesora CPU i wyświetlić podział użycia procesora CPU poszczególnych funkcji. Możesz wyświetlić wyniki użycia procesora CPU podczas wykonywania jest wstrzymany, na przykład w punkcie przerwania.

Poniższe instrukcje przedstawiają sposób użycia **użycie procesora CPU** narzędzia bez debugera za pomocą programu Visual Studio **Profiler wydajności**. W przykładach użyto kompilację wydania na komputerze lokalnym. Kompilacje wydania zapewniają najlepsze widoku wydajności rzeczywistych aplikacji. Aby Analizowanie użycia procesora CPU, korzystając z kompilacji debugowania, zobacz [profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md).

Zazwyczaj komputer lokalny najlepsze replikuje wykonywanie zainstalowanych aplikacji. W przypadku aplikacji Windows Phone zbieranie danych bezpośrednio z urządzenia zapewnia najbardziej dokładnych danych. Aby zebrać dane z urządzenia zdalnego, uruchom aplikację bezpośrednio na urządzeniu, nie za pośrednictwem połączenia pulpitu zdalnego.

>[!NOTE]
>Windows 7 lub nowszy jest wymagany do użycia [Profiler wydajności](../profiling/profiling-feature-tour.md).

##  <a name="collect-cpu-usage-data"></a>Zbieranie danych użycia procesora CPU

1. W projekcie programu Visual Studio, należy ustawić Konfiguracja rozwiązania **wersji** i wybierz **komputera lokalnego** jako cel wdrożenia.

    ![Wybieranie wersji i komputer lokalny](../profiling/media/cpuuse_selectreleaselocalmachine.png "wybierz wersji i komputer lokalny")

1. Wybierz **debugowania** > **Profiler wydajności**.

1. W obszarze **dostępnych narzędzi**, wybierz opcję **użycie procesora CPU**, a następnie wybierz pozycję **Start**.

    ![Wybierz użycie procesora CPU](../profiling/media/cpuuse_lib_choosecpuusage.png "wybierz użycie procesora CPU")

4. Po uruchomieniu aplikacji, sesji diagnostycznej rozpoczyna się i wyświetla dane użycia procesora CPU. Po zakończeniu zbierania danych wybierz **Zatrzymaj Kolekcjonowanie**.

   ![Zatrzymaj zbieranie danych użycia procesora CPU](../profiling/media/cpu_use_wt_stopcollection.png "zbierania danych użycia procesora CPU Stop")

   Narzędzie użycie procesora CPU analizuje dane i wyświetla raport.

   ![Raport użycia procesora CPU](../profiling/media/cpu_use_wt_report.png "raport użycia procesora CPU")


## <a name="analyze-the-cpu-usage-report"></a>Analizowanie raportu użycia procesora CPU

Raport diagnostyczny są posortowane według **łączny czas Procesora**, od najwyższego do najniższego. Zmień kolejność sortowania lub Sortuj kolumny, wybierając nagłówków kolumn. Użyj **filtru** listę rozwijaną, aby zaznacz lub odznacz opcję wątków, wyświetlać i używać **wyszukiwania** wyszukać określonego wątku lub węzeł.

###  <a name="BKMK_Call_tree_data_columns"></a> Kolumny danych użycia procesora CPU

|||
|-|-|
|**Łączny czas Procesora [jednostka, %]**|![Łączna liczba % danych równania](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Milisekund i procent użycia procesora CPU, używany przez wywołania do funkcji i funkcji wywoływanych przez funkcję w wybranym zakresie czasu. To różni się od **wykorzystanie procesora CPU** wykres osi czasu, który porównuje łączną aktywność procesora CPU w zakresie czasu, aby łączna liczba dostępne możliwości procesora CPU.|
|**Czas własny Procesora [jednostka, %]**|![Równania własnym %](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Milisekund i procent użycia procesora CPU, używany przez wywołania do funkcji w wybranym zakresie czasu, z wyjątkiem funkcji wywołanych przez funkcję.|
|**Module**|Nazwa modułu zawierający funkcję.

###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Użycie procesora CPU drzewo wywołań

Aby wyświetlić drzewo wywołań, wybierz węzeł nadrzędny w raporcie. **Użycie procesora CPU** zostanie otwarta strona **wywołujący/wywoływany** widoku. W **bieżący widok** listy rozwijanej wybierz **drzewo wywołań**.

####  <a name="BKMK_Call_tree_structure"></a> Struktura drzewa wywołań

 ![Wywołania struktury drzewa](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "struktury drzewa wywołań")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołanie użycie procesora CPU jest pseudo-węzła.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|W przypadku większości aplikacji gdy **Pokaż kod zewnętrzny** opcja jest wyłączona, węzeł drugiego poziomu, który jest **[kod zewnętrzny]** węzła. Węzeł zawiera system i platforma kod, który uruchamia i zatrzymuje aplikację, rysuje interfejsu użytkownika, kontroluje planowanie wątków i zapewnia inne niskopoziomowe usługi dla aplikacji.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu są asynchroniczne procedur, które są nazywane lub utworzonych przez system drugiego poziomu oraz kodu struktury i metody kod użytkownika.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Węzły podrzędne metody ma danych tylko w przypadku wywołania metody nadrzędnej. Gdy **Pokaż kod zewnętrzny** jest wyłączona, metody aplikacja może również zawierać **[kod zewnętrzny]** węzła.|

####  <a name="BKMK_External_Code"></a> Kod zewnętrzny

 System i platforma funkcje, które są wykonywane w kodzie są nazywane *kod zewnętrzny*. Funkcje kodu zewnętrznego Uruchom i Zatrzymaj aplikację, rysowania interfejsu użytkownika, kontrolować wątki i podaj inne niskopoziomowe usługi dla aplikacji. W większości przypadków nie chcesz kodu zewnętrznego, dzięki czemu użycie procesora CPU wywoływać drzewa zbiera informacje funkcji zewnętrznych metody użytkownika w jednym **[kod zewnętrzny]** węzła.

 Aby wyświetlić wywołania ścieżek kodu zewnętrznego na stronie głównej raport diagnostyczny (w okienku po prawej stronie), wybierz **Pokaż kod zewnętrzny** z **filtru** listy rozwijanej, a następnie wybierz pozycję **Zastosuj**. **Drzewo wywołań** widoku **użycie procesora CPU** strony następnie rozwija wywołania kodu zewnętrznego. ( **Filtru** listy rozwijanej jest dostępny na stronie głównej diagnostycznych, nie szczegółowe widoki.)

 ![Pokaż kod zewnętrzny](../profiling/media/cpu_use_wt_filterview.png "Pokaż kod zewnętrzny")

 Wiele łańcuchy wywołania kodu zewnętrznego głęboko zagnieżdżone, więc szerokość łańcucha może być dłuższa niż szerokość ekranu **nazwy funkcji** kolumny. Nazwy funkcji wtedy być wyświetlana jako **...** .

 ![Zagnieżdżony kod zewnętrzny, w drzewie wywołań](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "zagnieżdżony kod zewnętrzny, w drzewie wywołań")

 Aby znaleźć nazwę funkcji, których szukasz, użyj pola wyszukiwania. Umieść kursor nad wybranego wiersza, lub użyj poziomych pasków przewijania, aby wyświetlić dane.

 ![Wyszukaj zagnieżdżonego kodu zewnętrznego](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "wyszukiwanie zagnieżdżonego kodu zewnętrznego")

###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funkcje asynchroniczne użycia procesora CPU w drzewie wywołań

 Gdy kompilator napotka metody asynchronicznej, tworzy ukrytej klasy, aby kontrolować wykonywanie metody. Koncepcyjnie klasa jest automatu stanów. Klasa ma funkcje generowane przez kompilator, wywołujące asynchronicznie oryginalnej metody i wywołania zwrotne, harmonogram i Iteratory potrzebnych do ich uruchomienia. Gdy metoda nadrzędnego wywołuje pierwotną metodą, kompilator usuwa metodę z kontekstu wykonania elementu nadrzędnego i uruchamia metody ukrytej klasy w kontekście systemu i struktury kodu, który kontroluje wykonywanie aplikacji. Metody asynchroniczne są często, ale nie zawsze wykonywane w różnych wątkach co najmniej jeden. Ten kod, który pojawia się w **użycie procesora CPU** drzewo wywołań jako elementy podrzędne **[kod zewnętrzny]** węzeł bezpośrednio pod górny węzeł drzewa.

W poniższym przykładzie pierwsze dwa węzły w obszarze **[kod zewnętrzny]** są generowane przez kompilator metody klasy maszyny stanu. Trzeci węzeł jest wywołanie do oryginalnej metody.

![Asynchroniczne węzła](media/cpu_use_wt_getmaxnumberasync_selected.png "asynchronicznego węzła")

Rozwiń wygenerowane metody, aby pokazać, co się dzieje:

![Rozwinięty węzeł asynchroniczne](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "rozwinięte asynchronicznego węzła")

- `MainPage::GetMaxNumberAsyncButton_Click` po prostu zarządza listą wartości zadania, oblicza maksymalną liczbę wyników i wyświetla dane wyjściowe.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` Dowiesz się, działania wymagane do planowania i uruchamiania zadań 48, które opakować wywołanie `GetNumberAsync`.

- `MainPage::<GetNumberAsync>b__b` aktywnością zadania, które wywołują `GetNumber`.
