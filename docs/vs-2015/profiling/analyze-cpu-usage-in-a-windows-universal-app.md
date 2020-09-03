---
title: Analizowanie użycia procesora w aplikacji uniwersalnej systemu Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: def581f547db19a8db4cebc4d63739ff09bb5fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531667"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analizowanie użycia procesora w aplikacji uniwersalnej systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Jeśli musisz zbadać problemy z wydajnością w aplikacji, dobrym miejscem do rozpoczęcia jest zrozumienie, jak korzysta z procesora CPU. Narzędzie **użycie procesora CPU** pokazuje, gdzie procesor spędza czas wykonywania kodu. Aby skoncentrować się na określonych scenariuszach, użycie procesora CPU może być uruchamiane za pomocą narzędzia do [reagowania na czas odpowiedzi interfejsu użytkownika XAML](https://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) , narzędzia [użycie procesora CPU](../profiling/cpu-usage.md) lub obu narzędzi w pojedynczej sesji diagnostycznej.  
  
> [!NOTE]
> Narzędzie **użycie procesora CPU** nie może być używane z Windows Phone aplikacjami Silverlight 8,1.  
  
 W tym instruktażu przedstawiono proces zbierania i analizowania użycia procesora dla prostej aplikacji uniwersalnej XAML systemu Windows.  
  
## <a name="create-the-cpuusedemo-project"></a><a name="BKMK_Create_the_CpuUseDemo_project"></a> Tworzenie projektu CpuUseDemo  
 **CpuUseDemo** to aplikacja, która została utworzona w celu zademonstrowania sposobu zbierania i analizowania danych użycia procesora. Przyciski generują liczbę przez wywołanie metody, która wybiera wartość maksymalną z wielu wywołań do funkcji. Wywołana funkcja tworzy bardzo dużą liczbę losowych wartości, a następnie zwraca ostatnią. Dane są wyświetlane w polu tekstowym.  
  
1. Utwórz nowy projekt C# aplikacji uniwersalnej systemu Windows o nazwie **CpuUseDemo** przy użyciu szablonu **BlankApp** .  
  
     ![Tworzenie CpuUseDemoProject](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. Zastąp MainPage. XAML [tym kodem](#BKMK_MainPage_xaml).  
  
3. Zastąp MainPage.xaml.cs [tym kodem](#BKMK_MainPage_xaml_cs).  
  
4. Skompiluj aplikację i wypróbuj ją. Aplikacja jest wystarczająco prosta, aby pokazać typowe przypadki analizy danych użycia procesora CPU.  
  
## <a name="collect-cpu-usage-data"></a><a name="BKMK_Collect_CPU_usage_data"></a> Zbieranie danych użycia procesora CPU  
 ![Uruchom kompilację wydania aplikacji w symulatorze](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. W programie Visual Studio Ustaw cel wdrożenia na **symulatorze** i konfigurację rozwiązania do **wydania**.  
  
   - Uruchomienie aplikacji w symulatorze pozwala łatwo przełączać się między aplikacją a środowiskiem IDE programu Visual Studio.  
  
   - Uruchomienie tej aplikacji w trybie **wersji** zapewnia lepszy widok rzeczywistej wydajności aplikacji.  
  
2. W menu **debugowanie** wybierz pozycję **Profiler wydajności.**...  
  
3. W centrum wydajności i diagnostyki wybierz pozycję **użycie procesora** , a następnie wybierz polecenie **Uruchom**.  
  
    ![Rozpocznij sesję diagnostyczną CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Po uruchomieniu aplikacji kliknij pozycję **Pobierz maksymalną liczbę**. Odczekaj około sekundy po wyświetleniu danych wyjściowych, a następnie wybierz pozycję **Pobierz maksymalną liczbę asynchroniczną**. Oczekiwanie między kliknięciami przycisku ułatwia odizolowanie przycisku kliknij procedury w raporcie diagnostycznym.  
  
5. Po wyświetleniu drugiego wiersza danych wyjściowych wybierz pozycję **Zatrzymaj zbieranie** w centrum wydajności i diagnostyki.  
  
   ![Zatrzymaj zbieranie danych CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Narzędzie użycie procesora CPU analizuje dane i wyświetla raport.  
  
   ![Raport CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a><a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analizowanie raportu użycia procesora CPU  
  
### <a name="cpu-utilization-timeline-graph"></a><a name="BKMK_CPU_utilization_timeline_graph"></a> Wykres osi czasu użycia procesora CPU  
 ![Wykres CpuUtilization &#40;% &#41; osi czasu](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Wykres użycia procesora CPU przedstawia aktywność procesora CPU aplikacji jako procent całego czasu procesora CPU ze wszystkich rdzeni procesora na urządzeniu. Dane tego raportu zostały zebrane na maszynie dwurdzeniowej. Dwa duże wartości maksymalne reprezentują aktywność procesora dwukrotnego kliknięcia przycisku. `GetMaxNumberButton_Click` wykonuje synchronicznie na pojedynczym rdzeń, aby mieć sens, że wysokość grafu metody nigdy nie przekracza 50%. `GetMaxNumberAsycButton_Click` działa asynchronicznie w obu rdzeniach, dlatego należy ponownie wyszukać, że jego skok jest bliższy do wykorzystania wszystkich zasobów procesora CPU w obu rdzeniach.  
  
#### <a name="select-timeline-segments-to-view-details"></a><a name="BKMK_Select_timeline_segments_to_view_details"></a> Wybierz segmenty osi czasu, aby wyświetlić szczegóły  
 Użyj słupków wyboru na osi czasu **sesji diagnostycznej** , aby skoncentrować się na danych GetMaxNumberButton_Click:  
  
 ![GetMaxNumberButton&#95;kliknij pozycję zaznaczone](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 Oś czasu **sesji diagnostycznej** wyświetla teraz czas spędzony w wybranym segmencie (bit więcej niż 2 sekundy w tym raporcie) i filtruje drzewo wywołań do tych metod, które zostały uruchomione w zaznaczeniu.  
  
 Teraz wybierz `GetMaxNumberAsyncButton_Click` Segment.  
  
 ![GetMaxNumberAsyncButton&#95;kliknij pozycję Zgłoś zaznaczenie](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Ta metoda wykonuje około sekund szybciej niż `GetMaxNumberButton_Click` , ale znaczenie wpisów drzewa wywołań jest mniej oczywiste.  
  
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
 Kod zewnętrzny składa się z funkcji w składnikach system i Framework, które są wykonywane przez zapisanie kodu. Kod zewnętrzny zawiera funkcje, które uruchamiają i zatrzymują aplikację, rysują interfejs użytkownika, sterują wątkami i dostarczają do aplikacji inne usługi niskiego poziomu. W większości przypadków nie jest interesujący kod zewnętrzny, dlatego drzewo wywołań użycia procesora zbiera funkcje zewnętrzne metody użytkownika w jednym węźle **[kod zewnętrzny]** .  
  
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
  
## <a name="next-steps"></a><a name="BKMK_Next_steps"></a> Następne kroki  
 Aplikacja CpuUseDemo nie jest najbardziej doskonałymi aplikacjami, ale można ją rozłożyć przy użyciu tego narzędzia, aby eksperymentować z operacją asynchroniczną i innymi narzędziami w centrum wydajności i diagnostyki.  
  
- Należy pamiętać, że `MainPage::<GetNumberAsync>b__b` spędza więcej czasu w [kodzie zewnętrznym] niż wykonuje metodę GetNumber. Większość tego czasu jest obciążeniem operacji asynchronicznych. Spróbuj zwiększyć liczbę zadań (ustawionych w `NUM_TASKS` stałej MainPage.XAML.cs) i zmniejszyć liczbę iteracji w `GetNumber` (Zmień `MIN_ITERATIONS` wartość). Uruchom Scenariusz zbierania i porównaj aktywność procesora CPU z `MainPage::<GetNumberAsync>b__b` tym w oryginalnej sesji diagnostycznej użycia procesora CPU. Spróbuj zmniejszyć zadania i zwiększyć iteracje.  
  
- Użytkownicy często nie zadbają o rzeczywistą wydajność Twojej aplikacji. zapewniają one opiekę na postrzeganą wydajność i czas odpowiedzi aplikacji. Narzędzie do reagowania interfejsu użytkownika XAML pokazuje szczegóły działania w wątku interfejsu użytkownika, które mają wpływ na postrzegane czas odpowiedzi.  
  
     Utwórz nową sesję w centrum diagnostyki i wydajności, a następnie Dodaj narzędzie do reagowania na interfejs użytkownika XAML i narzędzie użycie procesora CPU. Uruchom Scenariusz zbierania. Jeśli ta czynność została przeczytana, prawdopodobnie raport nie wskazuje, co jeszcze nie zostało już zrobione, ale różnice w grafie osi czasu **wykorzystania wątku interfejsu użytkownika** dla dwóch metod są jednokrotne. W przypadku złożonych aplikacji w świecie połączenie narzędzi może być bardzo przydatne.  
  
## <a name="mainpagexaml"></a><a name="BKMK_MainPage_xaml"></a> MainPage. XAML  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
## <a name="mainpagexamlcs"></a><a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
