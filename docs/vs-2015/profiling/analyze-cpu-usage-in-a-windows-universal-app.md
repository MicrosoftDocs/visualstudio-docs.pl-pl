---
title: Analizowanie użycia procesora CPU w aplikacji Windows Universal | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fcc31e2f7fb06f58f07b0af58a1375466b16cc23
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053055"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analizowanie użycia procesora CPU w aplikacji Windows Universal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Jeśli musisz zbadać problemy z wydajnością w aplikacji, dobrym miejscem do rozpoczęcia jest zrozumienie, sposobem użycia procesora CPU. **Użycie procesora CPU** narzędzie pokazuje, gdzie Procesor spędza kodu w czasie wykonywania. Aby skoncentrować się na konkretnych scenariuszy, użycie procesora CPU można uruchomić z [czasu odpowiedzi interfejsu użytkownika XAML](http://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) narzędzia [zużycie energii](../profiling/analyze-energy-use-in-store-apps.md) narzędzia lub oba narzędzia w pojedynczej sesji diagnostycznej.  
  
> [!NOTE]
>  **Użycie procesora CPU** narzędzia nie można używać z aplikacji Windows Phone Silverlight 8.1.  
  
 Ten przewodnik przeprowadzi Cię przez zbieranie i analizowanie użycia procesora CPU dla prostej aplikacji Windows Universal XAML.  
  
## <a name="BKMK_Create_the_CpuUseDemo_project"></a> Utwórz projekt CpuUseDemo  
 **CpuUseDemo** to aplikacja, która została utworzona w celu zademonstrowania sposobu zbieranie i analizowanie danych użycia procesora CPU. Przyciski wygenerować liczbę, przez wywołanie metody, która wybiera maksymalną wartość z wielu wywołań do funkcji. Wywołana funkcja tworzy bardzo dużej liczby losowe wartości, a następnie zwraca ostatni z nich. Dane są wyświetlane w polu tekstowym.  
  
1. Utwórz nowy projekt aplikacji C# Windows Universal o nazwie **CpuUseDemo** przy użyciu **BlankApp** szablonu.  
  
     ![Tworzenie CpuUseDemoProject](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. Zastąp MainPage.xaml z [ten kod](#BKMK_MainPage_xaml).  
  
3. Zastąp MainPage.xaml.cs z [ten kod](#BKMK_MainPage_xaml_cs).  
  
4. Tworzenie aplikacji i wypróbuj jej działanie. Aplikacja jest proste pokazać Ci niektóre typowe przypadki użycia procesora CPU analizy danych.  
  
## <a name="BKMK_Collect_CPU_usage_data"></a> Zbieranie danych użycia procesora CPU  
 ![Uruchamianie kompilacji wydania aplikacji w symulatorze](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. W programie Visual Studio, Ustaw cel wdrożenia **symulator** i konfigurację rozwiązania na **wersji**.  
  
   - Uruchamianie aplikacji w symulatorze pozwala łatwo przełączać się między aplikacją i środowisku IDE programu Visual Studio.  
  
   - Ta aplikacja działa w **wersji** tryb zapewnia lepsze widok rzeczywistej wydajności aplikacji.  
  
2. Na **debugowania** menu, wybierz **Profiler wydajności...** .  
  
3. W Centrum wydajności i diagnostyki, wybierz **użycie procesora CPU** , a następnie wybierz **Start**.  
  
    ![Uruchamianie sesji diagnostyki CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Po uruchomieniu aplikacji, kliknij przycisk **uzyskać maksymalna liczba**. Poczekaj około sekundy po wyświetleniu danych wyjściowych, a następnie wybierz **uzyskać maksymalny numer Async**. Oczekiwania między kliknięć przycisków sprawia, że ułatwiają izolowanie przycisk kliknij procedur w raport diagnostyczny.  
  
5. Gdy zostanie wyświetlony drugi wiersz danych wyjściowych, wybierz **Zatrzymaj Kolekcjonowanie** w Centrum wydajności i diagnostyki.  
  
   ![Zatrzymaj zbieranie danych CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Narzędzie użycie procesora CPU analizuje dane i wyświetla raport.  
  
   ![Raport CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analizowanie raportu użycia procesora CPU  
  
### <a name="BKMK_CPU_utilization_timeline_graph"></a> Wykres osi czasu wykorzystania procesora CPU  
 ![CpuUtilization &#40;%&#41; wykres osi czasu](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Wykres wykorzystania procesora CPU pokazuje CPU działanie aplikacji jako procent cały czas procesora CPU ze wszystkich rdzeni procesora na urządzeniu. Na komputerze z procesorem dwurdzeniowym zbierania danych tego raportu. Dwie duże wartości szczytowe reprezentują aktywności Procesora dwóch kliknięć. `GetMaxNumberButton_Click` dokonuje synchronicznie jednordzeniowy, tak aby dobrym pomysłem, wysokość wykresu metody nigdy nie przekracza 50%. `GetMaxNumberAsycButton_Click` w obu rdzeni jest uruchamiane asynchronicznie, więc tak, aby ponownie wyglądał bezpośrednio, jego kolekcja pobiera bliżej przy użyciu wszystkich zasobów procesora CPU na obu rdzeni.  
  
#### <a name="BKMK_Select_timeline_segments_to_view_details"></a> Wybierz segmentów osi czasu, aby wyświetlić szczegóły  
 Użyj pasków zaznaczenia na **sesji diagnostycznej** osi czasu, aby skupić się na danych GetMaxNumberButton_Click:  
  
 ![GetMaxNumberButton&#95;kliknij wybrany](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 **Sesji diagnostycznej** osi czasu teraz Wyświetla czas potrzebny do wybranego segmentu (nieco więcej niż 2 sekundy, w tym raporcie) i filtruje drzewo wywołań do tych metod, które uruchomiono w zaznaczeniu.  
  
 Teraz wybierz `GetMaxNumberAsyncButton_Click` segmentu.  
  
 ![GetMaxNumberAsyncButton&#95;kliknij element raportu](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Ta metoda kończy około sekundy szybciej niż `GetMaxNumberButton_Click`, ale są mniej widocznych, znaczenie wpisy drzewo wywołań.  
  
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
 Kod zewnętrzny składa się z funkcji w składników systemu i framework, które są wykonywane przez kod, który można zapisać. Kod zewnętrzny zawiera funkcje, które Uruchom i Zatrzymaj aplikację, narysuj interfejsu użytkownika, kontrolować wątki i podaj inne niskopoziomowe usługi dla aplikacji. W większości przypadków nie będzie zainteresowani kod zewnętrzny, a więc użycie procesora CPU wywołać drzewa zbiera informacje funkcji zewnętrznych metody użytkownika w jednym **[kod zewnętrzny]** węzła.  
  
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
  
## <a name="BKMK_Next_steps"></a> Następne kroki  
 Aplikacja CpuUseDemo nie jest najbardziej doskonały aplikacji, ale jej narzędzia można rozszerzyć za pomocą Poeksperymentuj z operacją asynchroniczną i innych narzędzi w Centrum wydajności i diagnostyki.  
  
- Należy pamiętać, że `MainPage::<GetNumberAsync>b__b` zużywa więcej czasu w [kod zewnętrzny], niż wykonywanie metody GetNumber. Większość tego czasu to koszty operacji asynchronicznych. Spróbuj zwiększyć liczbę zadań (w `NUM_TASKS` stała MainPage.xaml.cs) i zmniejszając liczbę iteracji w `GetNumber` (zmiana `MIN_ITERATIONS` wartości). Uruchomić scenariusza zbieranie i porównywanie aktywności Procesora `MainPage::<GetNumberAsync>b__b`do tego w oryginalnej sesji diagnostyki użycia procesora CPU. Spróbuj zmniejszenie zadania i zwiększenie iteracje.  
  
- Użytkownicy często nie zachowaniu rzeczywistych wydajności aplikacji; są one istotne obserwowaną wydajność i szybkość reakcji aplikacji. Narzędzie XAML UI dynamiczne pokazuje szczegóły działań w wątku interfejsu użytkownika, że efekt postrzegany czas odpowiedzi.  
  
     Utwórz nową sesję w Centrum diagnostyki i wydajności, a następnie dodaj narzędzie XAML UI dynamiczne i narzędzie użycie procesora CPU. Uruchomić scenariusza z kolekcji. Jeśli znasz to znacznie, raport prawdopodobnie nie informujące, wszystkie elementy, które nie zostały jeszcze uznał, ale różnice w **wykorzystanie wątku interfejsu użytkownika** wykres osi czasu dla dwóch metod jest sprawdza się najlepiej. W aplikacji złożonych, rzeczywistych kombinacji narzędzi może być bardzo przydatne.  
  
## <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
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
  
## <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
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
