---
title: Analiza użycia procesora | Dokumenty firmy Microsoft
ms.custom: seodec18
ms.date: 04/02/2020
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88272af1733dbbaf7f46743388a8ecb6522e9f1a
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638836"
---
# <a name="analyze-cpu-usage"></a>Analizowanie użycia procesora CPU

Dobrym sposobem, aby rozpocząć badanie problemów z wydajnością w aplikacji jest zrozumienie jego użycia procesora CPU. Narzędzie **wydajności Użycie procesora CPU** pokazuje czas i procent spędzony na wykonywaniu kodu w językach C++, C#/Visual Basic i JavaScript.

Narzędzie **Użycie procesora CPU** można uruchomić w otwartym projekcie programu Visual Studio, w zainstalowanej aplikacji Microsoft Store lub dołączone do uruchomionej aplikacji lub procesu. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Narzędzie użycie **procesora CPU** można uruchomić z debugowaniem lub bez. W debugerze można włączać i wyłączać profilowanie procesora CPU i wyświetlać podział użycia procesora CPU dla różnych funkcji. Można wyświetlić wyniki użycia procesora CPU, gdy wykonanie jest wstrzymane, na przykład w punkcie przerwania.

Poniższe instrukcje pokazują, jak używać narzędzia **użycie procesora BEZ** debugera, przy użyciu programu Visual Studio **Performance Profiler**. Przykłady użyć Release kompilacji na komputerze lokalnym. Kompilacje wersji zapewniają najlepszy widok rzeczywistej wydajności aplikacji. Aby przeanalizować użycie procesora z kompilacjami debugowania, zobacz [Przewodnik dla początkujących dotyczący profilowania wydajności.](../profiling/beginners-guide-to-performance-profiling.md)

Zazwyczaj komputer lokalny najlepiej replikuje wykonanie zainstalowanej aplikacji. W przypadku aplikacji dla systemu Windows Phone zbieranie danych bezpośrednio z urządzenia zapewnia najdokładniejsze dane. Aby zbierać dane z urządzenia zdalnego, uruchom aplikację bezpośrednio na urządzeniu, a nie za pomocą połączenia pulpitu zdalnego.

>[!NOTE]
>System Windows 7 lub nowszy jest wymagany do korzystania z [programu Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="collect-cpu-usage-data"></a>Zbieranie danych dotyczących użycia procesora

1. W projekcie programu Visual Studio ustaw konfigurację rozwiązania na **Zwolnij** i wybierz **opcję Lokalny debuger systemu Windows** (lub Komputer **lokalny)** jako miejsce docelowe wdrożenia.

    ![Wybierz zwolnij i komputer lokalny](../profiling/media/cpuuse_selectreleaselocalmachine.png "Wybierz zwolnij i komputer lokalny")

1. Wybierz **pozycję Debug** > **Performance Profiler**.

1. W obszarze **Dostępne narzędzia**wybierz pozycję **Użycie procesora ,** a następnie wybierz pozycję **Start**.

    ![Wybieranie użycia procesora](../profiling/media/cpuuse_lib_choosecpuusage.png "Wybieranie użycia procesora")

4. Po uruchomieniu aplikacji rozpoczyna się sesja diagnostyczna i wyświetla dane użycia procesora CPU. Po zakończeniu zbierania danych wybierz pozycję **Zatrzymaj zbieranie**.

   ![Zatrzymywać zbieranie danych użycia procesora CPU](../profiling/media/cpu_use_wt_stopcollection.png "Zatrzymywać zbieranie danych użycia procesora CPU")

   Narzędzie Użycie procesora CPU analizuje dane i wyświetla raport.

   ![Raport użycia procesora CPU](../profiling/media/cpu_use_wt_report.png "Raport użycia procesora CPU")

## <a name="analyze-the-cpu-usage-report"></a>Analizowanie raportu użycia procesora CPU

Raport diagnostyczny jest sortowany według **całkowitego procesora CPU**, od najwyższego do najniższego. Zmień kolejność sortowania lub sortowanie kolumny, zaznaczając nagłówki kolumn. Użyj listy rozwijanej **Filtr,** aby zaznaczyć lub usunąć zaznaczenie wątków do wyświetlenia, a następnie użyj pola **Wyszukiwania,** aby wyszukać określony wątek lub węzeł.

::: moniker range=">=vs-2019"
Począwszy od programu Visual Studio 2019, można kliknąć **rozwiń gorącą ścieżkę** i **pokaż gorącą ścieżkę** przycisków, aby wyświetlić wywołania funkcji, które używają najwyższego procentu procesora CPU w widoku drzewa wywołań.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a>Kolumny danych użycia procesora CPU

|||
|-|-|
|**Całkowita wartość procesora CPU [jednostka, %]**|![Równanie danych ogółem %](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Milisekundy i procent procesora CPU używane przez wywołania funkcji i funkcje wywoływane przez funkcję w wybranym zakresie czasu. Różni się to od wykresu osi czasu **wykorzystania procesora CPU,** który porównuje całkowitą aktywność procesora CPU w zakresie czasu z całkowitą dostępną wydajnością PROCESORA CPU.|
|**Samoumiętowy procesor [jednostka, %]**|![Równanie własny procent](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Milisekundy i procent procesora CPU używane przez wywołania funkcji w wybranym zakresie czasu, z wyłączeniem funkcji wywoływanych przez funkcję.|
|**Moduł**|Nazwa modułu zawierającego funkcję.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a>Drzewo wywołań użycia procesora CPU

Aby wyświetlić drzewo wywołań, wybierz węzeł nadrzędny w raporcie. Zostanie otwarta strona **Użycie procesora CPU** w widoku **Wywołujący/Wywoływany.** W menu rozwijanym **Bieżący widok** wybierz polecenie **Drzewo wywołań**.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a>Wywołaj strukturę drzewa

::: moniker range=">=vs-2019"
![Wywołaj strukturę drzewa](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Wywołaj strukturę drzewa")
::: moniker-end
::: moniker range="vs-2017"
![Wywołaj strukturę drzewa](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Wywołaj strukturę drzewa")
::: moniker-end

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołań użycia procesora CPU jest pseudowęzkiem.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|W większości aplikacji, gdy opcja **Pokaż kod zewnętrzny** jest wyłączona, węzeł drugiego poziomu jest węzłem **[Kod zewnętrzny].** Węzeł zawiera kod systemu i struktury, który uruchamia i zatrzymuje aplikację, rysuje interfejs użytkownika, kontroluje planowanie wątków i zapewnia inne usługi niskiego poziomu do aplikacji.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu są metody kodu użytkownika i procedur asynchronicznych, które są wywoływane lub tworzone przez system drugiego poziomu i kod struktury.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Węzły podrzędne metody mają dane tylko dla wywołań metody nadrzędnej. Gdy **opcja Pokaż kod zewnętrzny** jest wyłączona, metody aplikacji mogą również zawierać węzeł **[Kod zewnętrzny].**|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a>Kod zewnętrzny

Funkcje systemowe i struktury, które są wykonywane przez kod są nazywane *kodem zewnętrznym*. Zewnętrzne funkcje kodu uruchomić i zatrzymać aplikację, narysuj interfejsu użytkownika, wątki kontroli i zapewnić inne usługi niskiego poziomu do aplikacji. W większości przypadków nie jesteś zainteresowany kodem zewnętrznym, więc drzewo wywołań użycia procesora CPU gromadzi funkcje zewnętrzne metody użytkownika w jednym węźle **[Kod zewnętrzny].**

Aby wyświetlić ścieżki wywołania kodu zewnętrznego, na głównej stronie raportu diagnostycznego (prawe okienko) wybierz pozycję **Pokaż kod zewnętrzny** z listy rozwijanej **Filtr,** a następnie wybierz pozycję **Zastosuj**. Widok **drzewa wywołań** na stronie **Użycie procesora CPU** następnie rozszerza wywołania kodu zewnętrznego. (Menu rozwijane **Filtr** jest dostępne na głównej stronie diagnostycznej, a nie w widokach szczegółowych).

![Pokaż kod zewnętrzny](../profiling/media/cpu_use_wt_filterview.png "Pokaż kod zewnętrzny")

Wiele zewnętrznych łańcuchów wywołań kodu są głęboko zagnieżdżone, więc szerokość łańcucha może przekroczyć szerokość wyświetlania **funkcji name** kolumny. Nazwy funkcji są następnie wyświetlane jako **...**.

![Zagnieżdżony kod zewnętrzny w drzewie wywołań](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Zagnieżdżony kod zewnętrzny w drzewie wywołań")

Aby znaleźć nazwę funkcji, której szukasz, użyj pola wyszukiwania. Umieść wskaźnik myszy na zaznaczonej linii lub użyj poziomego paska przewijania, aby wyświetlić dane.

::: moniker range=">=vs-2019"
![Wyszukiwanie zagnieżdżonego kodu zewnętrznego](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "Wyszukiwanie zagnieżdżonego kodu zewnętrznego")
::: moniker-end
::: moniker range="vs-2017"
![Wyszukiwanie zagnieżdżonego kodu zewnętrznego](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "Wyszukiwanie zagnieżdżonego kodu zewnętrznego")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>Funkcje asynchroniczne w drzewie wywołań użycia procesora CPU

 Gdy kompilator napotka metodę asynchronizacę, tworzy ukrytą klasę do kontrolowania wykonywania metody. Koncepcyjnie klasa jest maszyną stanu. Klasa ma funkcje generowane przez kompilator, które asynchronicznie wywołać oryginalne metody i wywołania zwrotne, harmonogram i iteratory potrzebne do ich uruchomienia. Gdy metoda nadrzędna wywołuje oryginalną metodę, kompilator usuwa metodę z kontekstu wykonywania nadrzędnego i uruchamia ukryte metody klasy w kontekście kodu systemu i struktury, który kontroluje wykonywanie aplikacji. Metody asynchroniczne są często, ale nie zawsze, wykonywane na jeden lub więcej różnych wątków. Ten kod pojawia się w drzewie wywołań **użycia procesora CPU** jako elementy podrzędne węzła **[Kod zewnętrzny]** bezpośrednio poniżej górnego węzła drzewa.

W poniższym przykładzie pierwsze dwa węzły w obszarze **[Kod zewnętrzny]** są metody generowane przez kompilator klasy maszyny stanu. Trzeci węzeł jest wywołaniem oryginalnej metody.

![Węzeł asynchroniczne](media/cpu_use_wt_getmaxnumberasync_selected.png "Węzeł asynchroniczne")

Rozwiń wygenerowane metody, aby pokazać, co się dzieje:

![Rozwinięty węzeł asynchroniczne](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Rozwinięty węzeł asynchroniczne")

- `MainPage::GetMaxNumberAsyncButton_Click`po prostu zarządza listą wartości zadań, oblicza maksymalną liczbę wyników i wyświetla dane wyjściowe.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext`pokazuje aktywność wymaganą do zaplanowania i uruchomienia 48 `GetNumberAsync`zadań, które zawijają połączenie do .

- `MainPage::<GetNumberAsync>b__b`pokazuje działanie zadań, które `GetNumber`wywołują .
