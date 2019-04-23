---
title: Użycie procesora CPU | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a78025bd11e56b001514f580acca18b7d21d5424
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067056"
---
# <a name="cpu-usage"></a>Użycie procesora CPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli musisz zbadać problemy z wydajnością w aplikacji, dobrym miejscem do rozpoczęcia jest zrozumienie, sposobem użycia procesora CPU. **Użycie procesora CPU** narzędzie pokazuje, gdzie Procesor spędza czasu wykonywania Visual C++, Visual C# / Visual Basic oraz kodu JavaScript.  
  
 Począwszy od programu Visual Studio 2015 Update 1, możesz zobaczyć podział użycia procesora CPU dla poszczególnych funkcji bez opuszczania debugera. Włącz profilowanie procesora CPU włączać i wyłączać podczas debugowania i wyświetlania wyników, gdy wykonanie zostanie zatrzymana, na przykład w punkcie przerwania. Aby uzyskać więcej informacji, zobacz [profilowanie Procesora w debugerze programu Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/profile-your-cpu-in-the-debugger-in-visual-studio-2015.aspx).  
  
 Aby uzyskać wskazówki, które analizuje wydajność aplikacji Windows Store, zobacz [Analizowanie użycia procesora CPU w aplikacjach Store](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 Centrum wydajności i diagnostyki oferuje wiele innych opcji do uruchamiania i zarządzania sesję diagnostyczną. Na przykład, można uruchomić **użycie procesora CPU** narzędzia na maszynach lokalnych lub zdalnych lub na w symulatorze lub w emulatorze. Można analizować wydajność Otwórz projekt w programie Visual Studio dołączony do uruchomionej aplikacji lub uruchomić aplikację, która jest instalowana z Store Windows. Aby uzyskać więcej informacji, zobacz [uruchamianie narzędzi profilowania bez debugowania](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
## <a name="BKMK_Collect_CPU_usage_data"></a> Zbieranie danych użycia procesora CPU  
  
1. W programie Visual Studio, należy ustawić Konfiguracja rozwiązania **wersji** i wybierz cel wdrożenia.  
  
    ![Wybieranie wersji i komputer lokalny](../profiling/media/cpuuse-selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
   - Aplikacja uruchomiona w **wersji** tryb zapewnia lepsze widok rzeczywistej wydajności aplikacji.  
  
   - Uruchamianie aplikacji na komputerze lokalnym, najlepiej replikuje wykonywanie zainstalowanych aplikacji.  
  
   - Jeśli dane są zbierane z urządzeniem zdalnym, uruchom aplikację bezpośrednio na urządzeniu, a nie za pomocą połączenia pulpitu zdalnego.  
  
   - W przypadku aplikacji Windows Phone, zbieranie danych bezpośrednio z **urządzenia** zapewnia najbardziej dokładnych danych.  
  
2. Na **debugowania** menu, wybierz **Profiler wydajności...** .  
  
3. Wybierz **użycie procesora CPU** , a następnie wybierz **Start**.  
  
    ![Wybierz opcję użycia procesora CPU](../profiling/media/cpuuse-lib-choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4. Po uruchomieniu aplikacji, kliknij przycisk **uzyskać maksymalna liczba**. Poczekaj około sekundy po wyświetleniu danych wyjściowych, a następnie wybierz **uzyskać maksymalny numer Async**. Oczekiwania między kliknięć przycisków sprawia, że ułatwiają izolowanie przycisk kliknij procedur w raport diagnostyczny.  
  
5. Gdy zostanie wyświetlony drugi wiersz danych wyjściowych, wybierz **Zatrzymaj Kolekcjonowanie** w Centrum wydajności i diagnostyki.  
  
   ![Zatrzymaj zbieranie danych CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Narzędzie użycie procesora CPU analizuje dane i wyświetla raport.  
  
   ![Raport CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analizowanie raportu użycia procesora CPU  
  
### <a name="BKMK_The_CPU_Usage_call_tree"></a> Użycie procesora CPU drzewo wywołań  
 Aby rozpocząć pracę, informacje o informacje na temat drzewa wywołań, wybierz ponownie `GetMaxNumberButton_Click` segmentu i spójrz na szczegóły drzewa wywołań.  
  
#### <a name="BKMK_Call_tree_structure"></a> Struktura drzewa wywołań  
 ![GetMaxNumberButton&#95;kliknij wywołanie drzewa](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołanie użycie procesora CPU jest pseudo-węzłem|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|W przypadku większości aplikacji gdy **Pokaż kod zewnętrzny** opcja jest wyłączona, węzeł drugiego poziomu, który jest **[kod zewnętrzny]** węzeł zawierający system i platforma kod, który uruchamia i zatrzymuje aplikację, rysuje interfejsu użytkownika kontroluje planowanie wątków i zapewnia inne niskopoziomowe usługi dla aplikacji.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Elementy podrzędne węzła drugiego poziomu są asynchroniczne procedur, które są nazywane lub utworzonych przez system drugiego poziomu oraz kodu struktury i metody kod użytkownika.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko w przypadku wywołania metody nadrzędnej. Gdy **Pokaż kod zewnętrzny** jest wyłączona, metody aplikacja może również zawierać **[kod zewnętrzny]** węzła.|  
  
#### <a name="BKMK_External_Code"></a> Kod zewnętrzny  
 Kod zewnętrzny są funkcjami w składnikach systemu i framework napisanego wykonywanych przez kod. Kod zewnętrzny obejmują funkcje, które Uruchom i Zatrzymaj aplikację, narysuj interfejsu użytkownika, kontrolować wątki i podaj inne niskopoziomowe usługi dla aplikacji. W większości przypadków nie będzie zainteresowani kod zewnętrzny, a więc użycie procesora CPU wywołać drzewa zbiera informacje funkcji zewnętrznych metody użytkownika w jednym **[kod zewnętrzny]** węzła.  
  
 Gdy chcesz wyświetlić ścieżki wywołanie kodu zewnętrznego, wybierz pozycję **Pokaż kod zewnętrzny** z **filtrowania widoku** listy, a następnie wybierz **Zastosuj**.  
  
 ![Wybierz Widok filtrów, a następnie Pokaż kod zewnętrzny](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Należy pamiętać, że wiele łańcuchy wywołania kodu zewnętrznego głęboko zagnieżdżone, tak, aby szerokość kolumny nazwy funkcji może być dłuższa niż szerokość wyświetlanie wszystkich pól poza największych monitorów komputera. W takim wypadku nazwy funkcji są wyświetlane jako **[...]** :  
  
 ![Zagnieżdżony kod zewnętrzny, w drzewie wywołań](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Użyj pola wyszukiwania, aby odnaleźć węzła, którego szukasz, a następnie użyj poziomych pasków przewijania do przenoszenia danych do wyświetlenia:  
  
 ![Wyszukaj zagnieżdżonego kodu zewnętrznego](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="BKMK_Call_tree_data_columns"></a> Kolumny danych drzewo wywołań  
  
|||  
|-|-|  
|**Łączny czas Procesora (%)**|![Łączna liczba % danych równania](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Procent aktywności procesora CPU przez aplikację w wybranym zakresie czasu użytego przez wywołania funkcji i funkcji wywoływanych przez funkcję. Należy pamiętać, że to różni się od **wykorzystanie procesora CPU** wykres osi czasu, który porównuje łączną aktywność aplikacji w zakres czasu, aby całkowita dostępna pojemność procesora CPU.|  
|**Własny Procesora (%)**|![Równania własnym %](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Procent aktywności procesora CPU przez aplikację w wybranym zakresie czasu użytego przez wywołanie funkcji, z wyłączeniem aktywności funkcji wywołanych przez funkcję.|  
|**Łączny czas Procesora (ms)**|Liczba milisekund spędzonych wykonywaniu w wywołaniach funkcji w wybranym zakresie czasu i funkcje, które zostały wywołane przez funkcję.|  
|**Własny procesora CPU (ms)**|Liczba milisekund spędzonych wykonywaniu w wywołaniach funkcji w wybranym zakresie czasu i funkcje, które zostały wywołane przez funkcję.|  
|**Module**|Nazwa modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [kod zewnętrzny].|  
  
### <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funkcje asynchroniczne użycia procesora CPU w drzewie wywołań  
 Gdy kompilator napotka metody asynchronicznej, tworzy ukrytej klasy, aby kontrolować wykonywanie metody. Koncepcyjnie klasa jest automatu stanów, który zawiera listę generowanych przez kompilator funkcje asynchroniczne, wywoływanie operacji oryginalnej metody i wywołania zwrotne, harmonogram i Iteratory, trzeba je poprawnie. Oryginalnej metody wywołanego przez nadrzędne metodę środowiska uruchomieniowego usuwa metodę z kontekstu wykonania elementu nadrzędnego, a następnie uruchamia metody klasy ukryte w kontekście systemu i struktury kodu, który kontrolować wykonywanie aplikacji. Metody asynchroniczne są często, ale nie zawsze wykonywane w różnych wątkach co najmniej jeden. Ten kod jest wyświetlany w drzewie wywołań użycie procesora CPU jako elementy podrzędne **[kod zewnętrzny]** węzeł bezpośrednio pod górny węzeł drzewa.  
  
 Aby to zobaczyć, w tym przykładzie, wybierz ponownie `GetMaxNumberAsyncButton_Click` segment na osi czasu.  
  
 ![GetMaxNumberAsyncButton&#95;kliknij element raportu](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Pierwsze dwa węzły w obszarze **[kod zewnętrzny]** są generowane przez kompilator metody klasy maszyny stanu. Trzeci to wywołanie do oryginalnej metody. Rozwijanie wygenerowane metody dowiesz się, co się dzieje.  
  
 ![Rozwinięte GetMaxNumberAsyncButton&#95;kliknij wywołanie drzewa](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` bardzo niewiele; jego zarządza listą wartości zadania, oblicza maksymalną liczbę wyników i wyświetla dane wyjściowe.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` Dowiesz się, działania wymagane do planowania i uruchamiania zadań 48, które opakować wywołanie `GetNumberAsync`.  
  
- `MainPage::<GetNumberAsync>b__b` Dowiesz się, aktywności zadań, które wywołują `GetNumber`.
