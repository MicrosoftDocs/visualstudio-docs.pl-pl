---
title: Analizowanie użycia procesora | Microsoft Docs
ms.custom: seodec18
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5ab97f3db8e5d44aa649455c313a5681ed93c8c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543393"
---
# <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora CPU

Dobrym sposobem na rozpoczęcie badania problemów z wydajnością w aplikacji jest zrozumienie użycia procesora CPU. Narzędzie wydajności **użycie procesora CPU** przedstawia czas procesora i procent poświęcany na wykonywanie kodu w języku C++, C#/Visual Basic i JavaScript.

Narzędzie **użycie procesora CPU** można uruchomić w otwartym projekcie programu Visual Studio, w zainstalowanej aplikacji Microsoft Store lub dołączone do uruchomionej aplikacji lub procesu. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Możesz uruchomić narzędzie **użycie procesora CPU** z debugowaniem lub bez niego. W debugerze można włączać i wyłączać profilowanie procesora CPU oraz wyświetlać podział na funkcję użycia procesora CPU. Można wyświetlić wyniki użycia procesora CPU po wstrzymaniu wykonywania, na przykład w punkcie przerwania.

W poniższych instrukcjach pokazano, jak używać narzędzia **użycie procesora CPU** bez debugera przy użyciu **profilera wydajności**programu Visual Studio. Przykłady wykorzystują kompilację wydania na komputerze lokalnym. Kompilacje wydań zapewniają najlepszy widok rzeczywistej wydajności aplikacji. Aby analizować użycie procesora przy użyciu kompilacji debugowania, zapoznaj [się z przewodnikiem dla początkujących do profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md).

Zazwyczaj komputer lokalny najlepiej replikuje zainstalowaną realizację aplikacji. W przypadku aplikacji Windows Phone zbieranie danych bezpośrednio z urządzenia zapewnia najbardziej dokładne dane. Aby zebrać dane z urządzenia zdalnego, uruchom aplikację bezpośrednio na urządzeniu, a nie na Podłączanie pulpitu zdalnego.

>[!NOTE]
>Do korzystania z [profilera wydajności](../profiling/profiling-feature-tour.md)jest wymagany system Windows 7 lub nowszy.

## <a name="collect-cpu-usage-data"></a>Zbieranie danych użycia procesora CPU

1. W projekcie programu Visual Studio Ustaw konfigurację rozwiązania na **Zwolnij** i wybierz pozycję **lokalny debuger systemu Windows** (lub **komputer lokalny**) jako cel wdrożenia.

    ![Wybieranie wersji i komputera lokalnego](../profiling/media/cpuuse_selectreleaselocalmachine.png "Wybieranie wersji i komputera lokalnego")

1. Wybierz pozycję **Debuguj**  >  **wydajność Profiler**.

1. W obszarze **dostępne narzędzia**wybierz pozycję **użycie procesora**, a następnie wybierz pozycję **Uruchom**.

    ![Wybierz użycie procesora CPU](../profiling/media/cpuuse_lib_choosecpuusage.png "Wybierz użycie procesora CPU")

4. Po uruchomieniu aplikacji rozpocznie się sesja diagnostyczna, która wyświetla dane użycia procesora CPU. Po zakończeniu zbierania danych wybierz pozycję **Zatrzymaj zbieranie**.

   ![Zatrzymaj zbieranie danych użycia procesora CPU](../profiling/media/cpu_use_wt_stopcollection.png "Zatrzymaj zbieranie danych użycia procesora CPU")

   Narzędzie użycie procesora CPU analizuje dane i wyświetla raport.

   ![Raport użycia procesora CPU](../profiling/media/cpu_use_wt_report.png "Raport użycia procesora CPU")

## <a name="analyze-the-cpu-usage-report"></a>Analizowanie raportu użycia procesora CPU

Raport diagnostyczny jest sortowany według **łącznego czasu procesora**, od najwyższego do najniższego. Zmień kolejność sortowania lub Sortuj kolumnę, wybierając nagłówki kolumn. Użyj listy rozwijanej **Filtr** , aby wybrać lub usunąć wątki do wyświetlenia, a następnie użyj pola **wyszukiwania** , aby wyszukać określony wątek lub węzeł.

::: moniker range=">=vs-2019"
Począwszy od programu Visual Studio 2019, można kliknąć przycisk **Rozwiń ścieżkę gorącą** i Pokaż przycisk ze **ścieżką gorącą** , aby zobaczyć wywołania funkcji, które używają najwyższego procentu procesora CPU w widoku drzewa wywołań.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a>Kolumny danych użycia procesora CPU

|Nazwa|Opis|
|-|-|
|**Łącznie CPU [jednostka,%]**|![Całkowite równanie (%)](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Liczba milisekund i procent użycia procesora używany przez wywołania funkcji oraz funkcje wywoływane przez funkcję, w wybranym zakresie czasu. Różni się to od wykresu osi czasu **użycie procesora** , który porównuje łączną aktywność procesora CPU w przedziale czasu z całkowitym DOSTĘPnym procesorem CPU.|
|**Procesor CPU (jednostka,%])**|![Równanie własne%](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Wartość procentowa milisekund i procesora używana przez wywołania funkcji w wybranym zakresie czasu, z wyłączeniem funkcji wywoływanych przez funkcję.|
|**Moduł**|Nazwa modułu zawierającego funkcję.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a>Drzewo wywołań użycia procesora CPU

Aby wyświetlić drzewo wywołań, wybierz węzeł nadrzędny w raporcie. Na stronie **użycie procesora CPU** zostanie otwarta widok **wywołujący/wywoływany** . Z listy rozwijanej **bieżący widok** wybierz pozycję **drzewo wywołań**.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a>Struktura drzewa wywołań

::: moniker range=">=vs-2019"
![Struktura drzewa wywołań](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Struktura drzewa wywołań")
::: moniker-end
::: moniker range="vs-2017"
![Struktura drzewa wywołań](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Struktura drzewa wywołań")
::: moniker-end

|Image (Obraz)|Opis|
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołań użycia procesora CPU jest pseudo-węzłowym.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|W większości aplikacji, gdy opcja **Pokaż zewnętrzny kod** jest wyłączona, węzeł drugiego poziomu jest węzłem **[kod zewnętrzny]** . Węzeł zawiera kod systemu i struktury, który rozpoczyna i kończy działanie aplikacji, rysuje interfejs użytkownika, kontroluje harmonogram wątków i udostępnia inne usługi niskiego poziomu aplikacji.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu to metody kodu użytkownika i procedury asynchroniczne, które są wywoływane lub tworzone przez system i kod struktury drugiego poziomu.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Węzły podrzędne metody mają tylko dane dla wywołań metody nadrzędnej. Gdy **Pokaż zewnętrzny kod** jest wyłączony, metody aplikacji mogą również zawierać węzeł **[kod zewnętrzny]** .|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a>Kod zewnętrzny

Funkcje systemowe i środowiskowe, które są wykonywane przez kod, są nazywane *kodem zewnętrznym*. Funkcje kodu zewnętrznego uruchamiają i zatrzymują aplikację, rysują interfejs użytkownika, wątkowość formantów i zapewniają innym usług niskiego poziomu aplikacji. W większości przypadków nie interesuje Cię kod zewnętrzny, dlatego drzewo wywołań użycia procesora zbiera funkcje zewnętrzne metody użytkownika w jednym węźle **[kod zewnętrzny]** .

Aby wyświetlić ścieżki wywołań kodu zewnętrznego, na głównej stronie raportu diagnostycznego (w okienku po prawej) wybierz pozycję **Pokaż kod zewnętrzny** z listy rozwijanej **Filtr** , a następnie wybierz pozycję **Zastosuj**. Widok **drzewa wywołań** na stronie **użycie procesora CPU** rozszerza wywołania kodu zewnętrznego. (Menu rozwijane **filtru** jest dostępne na głównej stronie diagnostycznej, a nie w widokach szczegółowych).

![Pokaż kod zewnętrzny](../profiling/media/cpu_use_wt_filterview.png "Pokaż kod zewnętrzny")

Wiele łańcuchów wywołań kodu zewnętrznego jest głęboko zagnieżdżonych, więc szerokość łańcucha może przekroczyć szerokość wyświetlania kolumny **nazwa funkcji** . Nazwy funkcji są wyświetlane jako **...**.

![Zagnieżdżony kod zewnętrzny w drzewie wywołań](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Zagnieżdżony kod zewnętrzny w drzewie wywołań")

Aby znaleźć nazwę funkcji, której szukasz, użyj pola wyszukiwania. Umieść kursor nad wybranym wierszem lub użyj poziomego paska przewijania, aby wyświetlić dane.

::: moniker range=">=vs-2019"
![Wyszukaj zagnieżdżony kod zewnętrzny](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "Wyszukaj zagnieżdżony kod zewnętrzny")
::: moniker-end
::: moniker range="vs-2017"
![Wyszukaj zagnieżdżony kod zewnętrzny](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "Wyszukaj zagnieżdżony kod zewnętrzny")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>Funkcje asynchroniczne w drzewie wywołań użycia procesora CPU

 Gdy kompilator napotka metodę asynchroniczną, tworzy ukrytą klasę do kontrolowania wykonywania metody. Koncepcyjnie, Klasa jest maszyną stanu. Klasa zawiera funkcje generowane przez kompilator, które asynchronicznie wywołują metody oryginalne, oraz wywołania zwrotne, harmonogram i Iteratory potrzebne do ich uruchomienia. Gdy metoda nadrzędna wywołuje oryginalną metodę, kompilator usuwa metodę z kontekstu wykonywania elementu nadrzędnego i uruchamia metody klasy ukrytej w kontekście kodu system i Framework, który kontroluje wykonywanie aplikacji. Metody asynchroniczne są często, ale nie zawsze, wykonywane w jednym lub wielu różnych wątkach. Ten kod jest wyświetlany w drzewie wywołań **użycia procesora** jako elementy podrzędne węzła **[kod zewnętrzny]** bezpośrednio poniżej górnego węzła drzewa.

W poniższym przykładzie pierwsze dwa węzły w **[kod zewnętrzny]** są metodami generowanymi przez kompilator klasy automatu Stanów. Trzeci węzeł jest wywołaniem metody oryginalnej.

![Węzeł asynchroniczny](media/cpu_use_wt_getmaxnumberasync_selected.png "Węzeł asynchroniczny")

Rozwiń wygenerowane metody, aby zobaczyć, co się dzieje:

![Rozwinięty węzeł asynchroniczny](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Rozwinięty węzeł asynchroniczny")

- `MainPage::GetMaxNumberAsyncButton_Click`program po prostu zarządza listą wartości zadania, oblicza maksymalną liczbę wyników i wyświetla dane wyjściowe.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext`przedstawia działanie wymagane do zaplanowania i uruchomienia 48 zadań, które zawijają wywołanie do `GetNumberAsync` .

- `MainPage::<GetNumberAsync>b__b`pokazuje aktywność zadań, które wywołują `GetNumber` .
