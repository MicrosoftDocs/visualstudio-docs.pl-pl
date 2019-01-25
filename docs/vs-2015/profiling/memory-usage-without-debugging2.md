---
title: Użycie pamięci bez Debugging2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4612325b467e92b40650d591b7d03bc611e66640
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765086"
---
# <a name="memory-usage-without-debugging"></a>Użycie pamięci bez debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć **użycie pamięci** narzędzia bez debugowania, aby wykonać następujące czynności  
  
- Monitorowanie aplikacji w pamięci podczas opracowywania scenariusza użycia bezpośrednio w programie Visual Studio.  
  
- Utworzyć szczegółowe migawki stanu pamięci aplikacji.  
  
- Porównywanie migawek do znalezienia głównej przyczyny problemów z pamięcią.  
  
  W tym temacie opisano sposób analizowania aplikacji w języku XAML Universal Windows za pomocą narzędzia użycie pamięci. Jeśli chcesz analizować wykorzystanie pamięci w aplikacjach Windows Universal, korzystające z języków JavaScript i HTML, zobacz [Analizowanie użycia pamięci (JavaScript)](http://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
##  <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a> Uruchamianie sesji diagnostyki użycia pamięci  
  
1.  Otwórz projekt Windows Universal C# w programie Visual Studio.  
  
2.  Na pasku menu wybierz **debugowanie / Profiler wydajności...** .  
  
3.  Wybierz **użycie pamięci** , a następnie wybierz **Start** znajdujący się u dołu strony.  
  
     ![Uruchamianie sesji diagnostyki użycie pamięci](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
##  <a name="BKMK_Monitor_memory_use"></a> Monitorowanie użycia pamięci  
 Chociaż można używać **użycie pamięci** narzędzie, aby wygenerować szczegółowe raporty, które służy do znajdowania i rozwiązywania problemów, możesz również służy do pamięci w czasie rzeczywistym skutki scenariusz aktywnie tworzysz.  
  
 Podczas uruchamiania sesji diagnostycznej uruchamiania aplikacji i **narzędzia diagnostyczne** okna wyświetlany jest wykres osi czasu użycia pamięci aplikacji.  
  
 ![Strona przeglądu użycia pamięci](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 Wykres osi czasu zawiera wahania pamięci aplikacji podczas jej działania. Skoki na wykresie zwykle wskazywać, że jakiś kod jest zbieranie lub tworzenie danych i odrzucanie go po zakończeniu przetwarzania. Duże wartości szczytowe wskazywać obszary, które mogą być w stanie zoptymalizować. Więcej częste jest wzrost użycia pamięci, które nie są zwracane, ponieważ może to oznaczać, nieefektywnego wykorzystania pamięci lub nawet przeciek pamięci.  
  
###  <a name="BKMK_Close_a_monitoring_session"></a> Zamknij sesję monitorowania  
 ![Zatrzymaj zbieranie](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 Aby zatrzymać sesji monitorowania bez tworzenia raportu, zamknij okno diagnostycznych. Aby wygenerować raport, po wykonaniu migawki pamięci, wybierz opcję **zatrzymać**.  
  
##  <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> Wykonywanie migawek stanu pamięci aplikacji  
 Jeśli wykryjesz problem pamięci, który chcesz zbadać również tworzyć migawek podczas sesji diagnostycznej do przechwytywania obiektów w pamięci, w szczególności momentach. Ponieważ aplikacja używa dużej liczby wiele typów obiektów, można skoncentrować się analizy na jeden scenariusz. Jest to również dobry pomysł, aby uzyskać migawkę odniesienia aplikacja przed wyświetleniem problem pamięci, innej migawki po pierwszym wystąpieniu problemu i co najmniej jednej migawki dodatkowe Jeśli można powtarzać tego scenariusza.  
  
 Aby zebrać migawki, należy uruchomić nowej sesji diagnostycznej. Wybierz **wykonać migawki** gdy zachodzi potrzeba przechwycenia danych pamięci. Aby wygenerować raport, wybierz opcję **zatrzymać**.  
  
##  <a name="BKMK_Memory_Usage_overview_page"></a> Strona przeglądu użycia pamięci  
 Po zatrzymaniu zbierania danych narzędzie użycie pamięci zatrzymuje aplikację i wyświetla raport o przegląd.  
  
 ![Strona przeglądu użycia pamięci](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
###  <a name="BKMK_Memory_Usage_snapshot_views"></a> Widoki migawki użycia pamięci  
 Używasz widoków migawki do otwierania szczegółowe raporty w nowych oknach programu Visual Studio. Istnieją dwa rodzaje widoków migawki:  
  
- A [migawki szczegóły raporty](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) zawiera typy i wystąpienia w jedną migawkę.  
  
- A [różnica (różnica) raporty migawki](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) porównuje typy i wystąpienia w dwóch migawek.  
  
  ![Wyświetl linki migawki](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  Ponumerowane elementy na ilustracji widoku migawki są łącza, które otwierają widoków raportów użycia pamięci.  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Tekst linku zawiera całkowita liczba bajtów w pamięci, gdy migawka została utworzona.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki posortowanej według całkowity rozmiar wystąpienia typu.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Tekst łącza zawiera całkowitą liczbę obiektów w pamięci, gdy migawka została utworzona.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki, który jest posortowana według liczby wystąpień typów.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Tekst łącza jest widoczna różnica między łączny rozmiar obiektów w pamięci w tej chwili tej migawki i całkowity rozmiar poprzednią migawkę.<br /><br /> Tekst łącza jest liczbą dodatnią, gdy rozmiar pamięci ta migawka jest większa niż poprzedniego i liczbą ujemną, jeśli rozmiar jest mniejszy. Tekst łącza **linii bazowej** wskazuje, że ta migawka jest pierwszy w sesji diagnostycznej; **Różnicy nie** wskazuje, że różnica wynosi zero.<br /><br /> Wybierz ten link, aby wyświetlić raport diff migawki posortowanej według różnica w łącznym rozmiarze wystąpień typów.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Tekst łącza jest widoczna różnica między całkowita liczba obiektów pamięci w tej migawce, a liczba obiektów w poprzedniej migawki.<br /><br /> Wybierz ten link, aby wyświetlić raport diff migawki posortowanej według różnica w łącznej liczbie wystąpień typów.|  
  
##  <a name="BKMK_Snapshot_reports"></a> Raporty migawek  
 ![Raport migawki użycia pamięci](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
###  <a name="BKMK_Snapshot_report_trees"></a> Drzewa raport migawki  
  
####  <a name="BKMK_Managed_Heap"></a> Sterta zarządzana  
 W drzewie sterty zarządzanej [sterty zarządzanej drzewa (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) i [sterty zarządzanej drzewa (różnica migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) wyświetlić typy i wystąpienia w raporcie. Wybierając typ lub wystąpienie Wyświetla **ścieżki do obiektu głównego** i **przywoływane obiekty** drzewa dla wybranego elementu.  
  
####  <a name="BKMK_Paths_to_Root"></a> Ścieżki do obiektu głównego  
 [Ścieżki do katalogu głównego drzewa (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) i [ścieżki do katalogu głównego drzewa (różnica migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) pokazuje łańcuch obiektów, które odwołują się typ lub wystąpienie. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.  
  
####  <a name="BKMK_Referenced_Objects"></a> Przywoływane obiekty  
 [Drzewa obiektów odwołania (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) i [drzewa przywoływane obiekty (różnica migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) Pokaż obiekty, które odwołuje się do wybranego typu lub wystąpienia.  
  
###  <a name="BKMK_Object_Type_and_Instance_fields"></a> Pola typu obiektu i wystąpienia  
 Gdy **typu obiektu** wpis ma podrzędnych wpisów, możesz wybrać ikonę strzałki aby je wyświetlić. Jeśli kolor **typu obiektu** niebieski tekst, możesz ją wybrać, aby przejść do obiektu w pliku kodu źródłowego. Plik źródłowy zostanie otwarty w osobnym oknie.  
  
 Nazwy są unikatowe identyfikatory, które są generowane przez narzędzie użycie pamięci.  
  
 Jeśli zauważysz typ, który nie może łatwo zidentyfikować lub jeśli nie wiesz, jak jest zaangażowana w kodzie, prawdopodobnie jest obiektem z .NET Framework, system operacyjny lub kompilatora, który wyświetla narzędzie użycie pamięci, ponieważ baza uczestniczy w łańcuchy własności obiekty.  
  
###  <a name="BKMK_Report_tree_filters_"></a> Filtry drzewa raportu  
 Większość aplikacji zawiera zaskakująco dużej liczby typów, z których większość nie są bardzo interesujące dla deweloperów aplikacji. **Użycie pamięci** narzędzie definiuje dwa filtry, które można użyć, aby ukryć większość z tych typów w **sterty zarządzanej** i **ścieżki do obiektu głównego** drzewa. Drzewo można również filtrować według nazwy typu.  
  
 ![Opcje sortowania i filtrowania](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
####  <a name="BKMK_Filter"></a> Filtr  
 Wprowadź ciąg w **filtru** pole, aby ograniczyć drzewa Wyświetla typy, które zawierają określony tekst. Filtr nie jest rozróżniana wielkość liter i rozpoznaje określonego ciągu w dowolnej części nazwy typu.  
  
####  <a name="BKMK_Collapse_Small_Objects"></a> Zwiń małe obiekty  
 Jeśli ten filtr jest stosowany, typów, których **rozmiar (w bajtach)** jest mniejszy niż 0,5% całkowitego rozmiaru pamięci migawki są ukryte w **sterty zarządzanej** listy.  
  
####  <a name="BKMK_Just_My_Code"></a> Tylko mój kod  
 **Tylko mój kod** filtr ukrywa największą liczbą wystąpień, które zostały wygenerowane przez kod zewnętrzny. Typy zewnętrzne należą przez system operacyjny lub składnikami ramach lub są generowane przez kompilator.  
  
##  <a name="BKMK_Snapshot_details_reports"></a> Migawka szczegóły raportów  
 Raport szczegóły migawki umożliwia skoncentrowanie się na jedną migawkę z sesji diagnostycznej. Aby otworzyć raport szczegóły, wybierz jedno z łączy w widoku migawki, jak pokazano na poniższej ilustracji. Oba łącza otworzyć ten sam raport; Jedyna różnica polega na kolejności sortowania począwszy od **sterty zarządzanej** drzewa w raporcie. W obu przypadkach można zmienić kolejność sortowania, po otwarciu raportu.  
  
 ![Łącza do migawki raportu w widoku migawki](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
-   **MB** łącze sortuje raport według **całkowity rozmiar (w bajtach)** kolumny.  
  
-   **Obiektów** łącze sortuje raport według **liczba** kolumny.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Zarządzane drzewa sterty (szczegóły migawki)  
 **Sterty zarządzanej** drzewa zawiera listę typów obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić 10 największych wystąpienia typu, posortowane według rozmiaru. Wybierając typ lub wystąpienie Wyświetla **ścieżki do obiektu głównego** i **przywoływane obiekty** drzewa dla wybranego elementu.  
  
 ![Zarządzanej sterty drzewa](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Typ obiektu**|Nazwa wystąpienia typu lub obiektu.|  
|**Liczba**|Liczba wystąpień obiektu tego typu. Numer ma zawsze numer 1, w przypadku wystąpienia.|  
|**Rozmiar (bajty)**|Dla typu, rozmiaru wszystkich wystąpień typu w migawce pamięci, z wyłączeniem rozmiar obiektów zawartych w przypadkach.<br /><br /> Dla wystąpienia typu, rozmiar obiektu, z wyłączeniem rozmiar obiektów zawartych w wystąpieniu. wystąpienia.|  
|**Całkowity rozmiar (w bajtach)**|Rozmiar wystąpienia typu lub rozmiaru pojedyncze wystąpienie, takich jak rozmiar zawartych obiektów.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Ścieżki do katalogu głównego drzewa (szczegóły migawki)  
 **Ścieżki do katalogu głównego drzewa** pokazuje łańcuch obiektów, które odwołują się typ lub wystąpienie. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.  
  
 ![Ścieżki do katalogu głównego drzewa dla typów](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Po wyświetleniu typu na **ścieżki do obiektu głównego** drzewa, liczba obiektów typów, które przechowują odwołania do tego typu jest wyświetlana w **licznik odwołań** kolumny. Kolumna nie jest wyświetlana podczas analizowania wystąpienia.  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Odwołania drzewa obiektów (szczegóły migawki)  
 **Przywoływane obiekty** drzewa zawiera obiekty, które odwołuje się do wybranego typu lub wystąpienia.  
  
 ![Odwołania drzewa Objjects dla wystąpień](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ obiektu / wystąpienie**|Nazwa wystąpienia typu lub obiektu.|  
|**Rozmiar (bajty)**|Dla typu, rozmiaru wszystkich wystąpień tego typu, z wyłączeniem rozmiar obiektów znajdujących się w typie.<br /><br /> W przypadku wystąpienia rozmiar obiektu, z wyłączeniem rozmiar obiektów zawartych w obiekcie.|  
|**Całkowity rozmiar (w bajtach)**|Całkowity rozmiar wystąpienia typu lub rozmiar wystąpienia, takich jak rozmiar zawartych obiektów.|  
  
##  <a name="BKMK_Snapshot_difference__diff__reports"></a> Raporty migawki różnica (różnica)  
 Raport migawki różnica (różnica) pokazuje zmiany między podstawowym migawką i migawką, która została wykonana bezpośrednio przed. Aby otworzyć raport różnic, wybierz jedno z łączy w widoku migawki, jak pokazano na poniższej ilustracji. Oba łącza otworzyć ten sam raport; Jedyna różnica polega na kolejności sortowania począwszy od **sterty zarządzanej** drzewa w raporcie. Po otwarciu raportu, możesz zmienić kolejność sortowania.  
  
 ![Łącza do różnicy raport w widoku migawki](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
-   **MB** łącze sortuje raport według **całkowity rozmiar (w bajtach)** kolumny.  
  
-   **Obiektów** łącze sortuje raport według **liczba** kolumny.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Zarządzane drzewa sterty (różnica migawki)  
 **Sterty zarządzanej** drzewa zawiera listę typów obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić 10 największych wystąpienia typu, posortowane według rozmiaru. Wybierając typ lub wystąpienie Wyświetla **ścieżki do obiektu głównego** i **przywoływane obiekty** drzewa dla wybranego elementu.  
  
 ![Zarządzane drzewa sterty dla typu w raporcie różnica](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Należy zauważyć, że **liczba**, **rozmiar (w bajtach)**, i **całkowity rozmiar (w bajtach)** kolumny mają zostały zwinięte na obrazie.  
  
|||  
|-|-|  
|**Typ obiektu**|Nazwa wystąpienia typu lub obiektu.|  
|**Liczba**|Liczba wystąpień typu podstawowego migawki. **Liczba** ma zawsze numer 1 dla wystąpienia.|  
|**Różnica liczby**|Dla typu, różnią się w liczbie wystąpień typu podstawowego migawki i poprzednią migawkę. To pole jest puste w przypadku wystąpienia.|  
|**Rozmiar (bajty)**|Rozmiar obiektów w migawce podstawowy, z wyłączeniem rozmiar obiektów znajdujące się w obiektach. Dla typu **rozmiar (w bajtach)** i **całkowity rozmiar (w bajtach)** są sumy rozmiarów wystąpień typu.|  
|**Diff całkowity rozmiar (w bajtach)**|Dla typu, różnią się w całkowity rozmiar wystąpienia typu podstawowego migawki i poprzednią migawkę, z wyłączeniem rozmiar obiektów zawartych w wystąpieniach. To pole jest puste w przypadku wystąpienia.|  
|**Całkowity rozmiar (w bajtach)**|Rozmiar obiektów w migawce podstawowego, takich jak rozmiar obiektów zawartych w obiektach.|  
|**Różnica w rozmiarze włącznie (w bajtach)**|Dla typu, różnią się rozmiar wszystkich wystąpień tego typu podstawowego migawki i poprzednią migawkę, takich jak rozmiar obiektów zawartych w obiektach. To pole jest puste w przypadku wystąpienia.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Ścieżki do katalogu głównego drzewa (różnica migawki)  
 **Ścieżki do katalogu głównego drzewa** pokazuje łańcuch obiektów, które odwołują się typ lub wystąpienie. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.  
  
 ![Ścieżki do katalogu głównego drzewa dla wystąpień w widoku różnic](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Odwołania drzewa obiektów (różnica migawki)  
 **Przywoływane obiekty** drzewa zawiera obiekty, które odwołuje się do typu podstawowego lub wystąpienia.  
  
 ![Odwołania drzewa Objjects dla wystąpień](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ obiektu / wystąpienie**|Nazwa wystąpienia typu lub obiektu.|  
|**Rozmiar (bajty)**|W przypadku wystąpienia rozmiar obiektu w migawce podstawowy, z wyłączeniem rozmiar obiektów zawartych w wystąpieniu.<br /><br /> Aby uzyskać typ całkowity rozmiar wystąpienia typu podstawowego migawki, z wyłączeniem rozmiar obiektów zawartych w wystąpieniu.|  
|**Całkowity rozmiar (w bajtach)**|Rozmiar obiektów w migawce podstawowego, takich jak rozmiar obiektów zawartych w obiektach.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pamięć języka JavaScript](../profiling/javascript-memory.md)   
 [Analizowanie wydajności aplikacji](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)   
 [Uruchamianie narzędzi diagnostycznych i wydajności](http://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [Wydajność — najlepsze rozwiązania dla aplikacji Windows Store przy użyciu języka C++, C# i Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Diagnozowanie problemów z pamięcią za pomocą nowe narzędzie użycie pamięci w programie Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706)
