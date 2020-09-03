---
title: Użycie procesora | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7732a5757281e83c501a8258dd1d44b4f329a87a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548060"
---
# <a name="cpu-usage"></a>Użycie procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli musisz zbadać problemy z wydajnością w aplikacji, dobrym miejscem do rozpoczęcia jest zrozumienie, jak korzysta z procesora CPU. Narzędzie **użycie procesora CPU** pokazuje, gdzie procesor spędza czas wykonywania Visual C++, Visual C#/Visual Basic i JavaScript Code.  
  
 Począwszy od programu Visual Studio 2015 Update 1, można zobaczyć podział poszczególnych funkcji użycia procesora CPU bez opuszczania debugera. Można włączać i wyłączać profilowanie procesora CPU podczas debugowania, a także wyświetlać wyniki po zatrzymaniu wykonywania, na przykład w punkcie przerwania. Aby uzyskać więcej informacji, zobacz [profilowanie procesora CPU w debugerze w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/profile-your-cpu-in-the-debugger-in-visual-studio-2015/).  
  
 Aby zapoznać się z przewodnikiem, który analizuje wydajność aplikacji ze sklepu Windows, zobacz [Analizowanie użycia procesora CPU w aplikacjach ze sklepu](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 Centrum wydajności i diagnostyki oferuje wiele innych opcji uruchamiania sesji diagnostycznej i zarządzania nią. Na przykład można uruchomić narzędzie **użycie procesora CPU** na maszynach lokalnych lub zdalnych albo w symulatorze lub emulatorze. Można analizować wydajność otwartego projektu w programie Visual Studio, dołączyć do uruchomionej aplikacji lub uruchomić aplikację, która jest zainstalowana ze sklepu Windows. Aby uzyskać więcej informacji, zobacz [Uruchamianie narzędzi profilowania bez debugowania](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
## <a name="collect-cpu-usage-data"></a><a name="BKMK_Collect_CPU_usage_data"></a> Zbieranie danych użycia procesora CPU  
  
1. W programie Visual Studio Ustaw konfigurację rozwiązania na **Zwolnij** i wybierz miejsce docelowe wdrożenia.  
  
    ![Wybieranie wersji i komputera lokalnego](../profiling/media/cpuuse-selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
   - Uruchomienie aplikacji w trybie **wydania** zapewnia lepszy widok rzeczywistej wydajności aplikacji.  
  
   - Uruchomienie aplikacji na komputerze lokalnym najlepiej replikuje wykonywanie zainstalowanej aplikacji.  
  
   - Jeśli zbierasz dane z urządzenia zdalnego, uruchom aplikację bezpośrednio na urządzeniu, a nie za pomocą Podłączanie pulpitu zdalnego.  
  
   - W przypadku aplikacji Windows Phone zbieranie danych bezpośrednio z **urządzenia** zapewnia najbardziej dokładne dane.  
  
2. W menu **debugowanie** wybierz pozycję **Profiler wydajności.**...  
  
3. Wybierz pozycję **użycie procesora** , a następnie wybierz polecenie **Uruchom**.  
  
    ![Wybierz użycie procesora CPU](../profiling/media/cpuuse-lib-choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4. Po uruchomieniu aplikacji kliknij pozycję **Pobierz maksymalną liczbę**. Odczekaj około sekundy po wyświetleniu danych wyjściowych, a następnie wybierz pozycję **Pobierz maksymalną liczbę asynchroniczną**. Oczekiwanie między kliknięciami przycisku ułatwia odizolowanie przycisku kliknij procedury w raporcie diagnostycznym.  
  
5. Po wyświetleniu drugiego wiersza danych wyjściowych wybierz pozycję **Zatrzymaj zbieranie** w centrum wydajności i diagnostyki.  
  
   ![Zatrzymaj zbieranie danych CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Narzędzie użycie procesora CPU analizuje dane i wyświetla raport.  
  
   ![Raport CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analizowanie raportu użycia procesora CPU  
  
### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> Drzewo wywołań użycia procesora CPU  
 Aby rozpocząć zrozumienie informacji o drzewie wywołań, należy wybrać `GetMaxNumberButton_Click` segment i sprawdzić szczegóły drzewa wywołań.  
  
#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Struktura drzewa wywołań  
 ![GetMaxNumberButton&#95;kliknij pozycję drzewo wywołań](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|Obraz|Opis|  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołań użycia procesora CPU jest pseudo-węzłem|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|W większości aplikacji, gdy opcja **Pokaż zewnętrzny kod** jest wyłączona, węzeł drugiego poziomu jest węzłem **[zewnętrzny kod]** zawierającym kod systemowy i program, który rozpoczyna i kończy działanie aplikacji, rysuje interfejs użytkownika, kontroluje planowanie wątków i udostępnia inne usługi niskiego poziomu aplikacji.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu to metody kodu użytkownika i procedury asynchroniczne, które są wywoływane lub tworzone przez system i kod struktury drugiego poziomu.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko dla wywołań metody nadrzędnej. Gdy **Pokaż zewnętrzny kod** jest wyłączony, metody aplikacji mogą również zawierać węzeł **[kod zewnętrzny]** .|  
  
#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Kod zewnętrzny  
 Kod zewnętrzny to funkcje w składnikach system i Framework, które są wykonywane przez zapisanie kodu. Kod zewnętrzny obejmuje funkcje, które uruchamiają i zatrzymują aplikację, rysują interfejs użytkownika, sterują wątkami i dostarczają do aplikacji inne usługi niskiego poziomu. W większości przypadków nie jest interesujący kod zewnętrzny, dlatego drzewo wywołań użycia procesora zbiera funkcje zewnętrzne metody użytkownika w jednym węźle **[kod zewnętrzny]** .  
  
 Aby wyświetlić ścieżki wywołań kodu zewnętrznego, wybierz pozycję **Pokaż kod zewnętrzny** z listy **widok filtru** , a następnie wybierz pozycję **Zastosuj**.  
  
 ![Wybierz widok filtru, a następnie Pokaż kod zewnętrzny](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Należy pamiętać, że wiele łańcuchów połączeń kodu zewnętrznego jest głęboko zagnieżdżonych, dzięki czemu szerokość kolumny nazwy funkcji może przekroczyć szerokość wyświetlania wszystkich, ale większość monitorów komputerów. W takim przypadku nazwy funkcji są wyświetlane jako **[...]**:  
  
 ![Zagnieżdżony kod zewnętrzny w drzewie wywołań](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Użyj pola wyszukiwania, aby znaleźć węzeł, którego szukasz, a następnie użyj poziomego paska przewijania, aby przenieść dane do widoku:  
  
 ![Wyszukaj zagnieżdżony kod zewnętrzny](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="call-tree-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> Zadzwoń do kolumn danych drzewa  
  
|Właściwość|Opis|
|-|-|  
|**Łączny czas procesora (%)**|![Całkowite równanie (%)](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Wartość procentowa aktywności procesora aplikacji w wybranym zakresie czasu, która była używana przez wywołania funkcji i funkcji wywoływanych przez funkcję. Należy zauważyć, że różni się to od wykresu czasu **użycia procesora CPU** , który porównuje łączną aktywność aplikacji w zakresie czasu z całkowitą dostępną pojemnością procesora.|  
|**Własny procesor CPU (%)**|![Równanie własne%](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Wartość procentowa aktywności procesora aplikacji w wybranym zakresie czasu, która była używana przez wywołania funkcji, z wyłączeniem działania funkcji wywoływanych przez funkcję.|  
|**Łączny czas procesora (MS)**|Liczba milisekund spędzonych na wywołaniach funkcji w wybranym zakresie czasu oraz funkcji, które zostały wywołane przez funkcję.|  
|**Procesor własny (MS)**|Liczba milisekund spędzonych na wywołaniach funkcji w wybranym zakresie czasu oraz funkcji, które zostały wywołane przez funkcję.|  
|**Moduł**|Nazwa modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [kod zewnętrzny].|  
  
### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funkcje asynchroniczne w drzewie wywołań użycia procesora CPU  
 Gdy kompilator napotka metodę asynchroniczną, tworzy ukrytą klasę do kontrolowania wykonywania metody. Koncepcyjnie, Klasa jest maszyną stanu, która zawiera listę funkcji generowanych przez kompilator, które asynchronicznie wywołują operacje oryginalnej metody, a także wywołania zwrotne, harmonogram i Iteratory, które są wymagane prawidłowo. Gdy oryginalna Metoda jest wywoływana przez metodę nadrzędną, środowisko uruchomieniowe usuwa metodę z kontekstu wykonywania elementu nadrzędnego i uruchamia metody klasy ukrytej w kontekście kodu systemowego i struktury kontrolującego wykonywanie aplikacji. Metody asynchroniczne są często, ale nie zawsze, wykonywane w jednym lub wielu różnych wątkach. Ten kod jest pokazywany w drzewie wywołań użycia procesora jako elementy podrzędne węzła **[kod zewnętrzny]** bezpośrednio poniżej górnego węzła drzewa.  
  
 Aby zobaczyć to w naszym przykładzie, należy wybrać segment na `GetMaxNumberAsyncButton_Click` osi czasu.  
  
 ![GetMaxNumberAsyncButton&#95;kliknij pozycję Zgłoś zaznaczenie](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Pierwsze dwa węzły w obszarze **[kod zewnętrzny]** są metodami generowanymi przez kompilator klasy automatu Stanów. Trzecia jest wywołaniem metody oryginalnej. Rozszerzanie wygenerowanych metod pokazuje, co się dzieje.  
  
 ![Rozwinięte GetMaxNumberAsyncButton&#95;kliknij pozycję drzewo wywołań](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` działa bardzo mało. zarządza listą wartości zadania, oblicza maksymalną liczbę wyników i wyświetla dane wyjściowe.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` przedstawia działanie wymagane do zaplanowania i uruchomienia 48 zadań, które zawijają wywołanie do `GetNumberAsync` .  
  
- `MainPage::<GetNumberAsync>b__b` pokazuje aktywność zadań, które wywołują `GetNumber` .
