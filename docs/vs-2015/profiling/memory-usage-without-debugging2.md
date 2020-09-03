---
title: Użycie pamięci bez Debugging2 | Microsoft Docs
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
ms.openlocfilehash: ce7d30b66106b8d0d861fcf782a77ee7f461196b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532044"
---
# <a name="memory-usage-without-debugging"></a>Użycie pamięci bez debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wykonać następujące czynności, można użyć narzędzia **użycie pamięci** bez debugowania.  
  
- Monitoruj bezpośrednio użycie pamięci przez aplikację w programie Visual Studio podczas opracowywania scenariusza.  
  
- Utwórz szczegółowe migawki stanu pamięci aplikacji.  
  
- Porównaj migawki, aby znaleźć główną przyczynę problemów z pamięcią.  
  
  W tym temacie opisano sposób użycia narzędzia użycie pamięci do analizowania uniwersalnej aplikacji języka XAML systemu Windows. Jeśli chcesz analizować użycie pamięci w aplikacjach uniwersalnych systemu Windows korzystających z języków JavaScript i HTML, zobacz [Analizowanie użycia pamięci (JavaScript)](https://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
## <a name="start-a-memory-usage-diagnostic-session"></a><a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a> Rozpocznij sesję diagnostyczną wykorzystania pamięci  
  
1. Otwórz projekt uniwersalny systemu Windows w języku C# w programie Visual Studio.  
  
2. Na pasku menu wybierz polecenie  **Debuguj/Profiler wydajności..**..  
  
3. Wybierz opcję **użycie pamięci** , a następnie wybierz przycisk **Start** w dolnej części strony.  
  
     ![Rozpocznij sesję diagnostyczną wykorzystania pamięci](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
## <a name="monitor-memory-use"></a><a name="BKMK_Monitor_memory_use"></a> Monitoruj użycie pamięci  
 Mimo że można użyć narzędzia **użycie pamięci** do generowania szczegółowych raportów, których można użyć do znajdowania i rozwiązywania problemów, można również użyć jej do badania efektów pamięci w czasie rzeczywistym scenariusza, który aktywnie opracowujesz.  
  
 Po uruchomieniu sesji diagnostycznej aplikacja zostanie uruchomiona, a w oknie **Narzędzia diagnostyczne** zostanie wyświetlony Graf osi czasu aplikacji.  
  
 ![Strona przegląd użycia pamięci](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 Wykres osi czasu pokazuje fluktuacje w pamięci aplikacji w trakcie jej działania. Skoki na wykresie zwykle wskazują, że jakiś kod zbiera lub tworzy dane, a następnie odrzuca je po zakończeniu przetwarzania. Duże skoki wskazują obszary, które mogą być optymalizowane. Jest to wzrost wykorzystania pamięci, który nie jest zwracany, ponieważ może wskazywać niewydajne użycie pamięci lub nawet przeciek pamięci.  
  
### <a name="close-a-monitoring-session"></a><a name="BKMK_Close_a_monitoring_session"></a> Zamykanie sesji monitorowania  
 ![Zatrzymaj zbieranie](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 Aby zatrzymać sesję monitorowania bez tworzenia raportu, po prostu Zamknij okno diagnostyki. Aby wygenerować raport po wykonaniu migawek pamięci, wybierz pozycję **Zatrzymaj**.  
  
## <a name="take-snapshots-of-the-memory-state-of-your-app"></a><a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> Tworzenie migawek stanu pamięci aplikacji  
 Jeśli wykryjesz problem z pamięcią, który chcesz zbadać, możesz wykonać migawki podczas sesji diagnostycznej, aby przechwytywać obiekty w pamięci w określonym momencie. Ponieważ aplikacja korzysta z dużej liczby typów obiektów, można skoncentrować się na analizie w jednym scenariuszu. Dobrym pomysłem jest również uzyskanie podstawowej migawki aplikacji przed pojawieniem się problemu z pamięcią, kolejną migawką po pierwszym wystąpieniu problemu oraz co najmniej jedną dodatkową migawek, jeśli można powtórzyć ten scenariusz.  
  
 Aby zebrać migawki, Rozpocznij nową sesję diagnostyczną. Wybierz pozycję **zrób migawkę** , aby przechwycić dane pamięci. Aby wygenerować raport, wybierz pozycję **Zatrzymaj**.  
  
## <a name="memory-usage-overview-page"></a><a name="BKMK_Memory_Usage_overview_page"></a> Strona przegląd użycia pamięci  
 Po zatrzymaniu zbierania danych narzędzie użycie pamięci zatrzyma aplikację i wyświetli raport z przeglądu.  
  
 ![Strona przegląd użycia pamięci](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
### <a name="memory-usage-snapshot-views"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> Widoki migawek użycia pamięci  
 Widoki migawek służą do otwierania szczegółowych raportów w nowych oknach programu Visual Studio. Istnieją dwa rodzaje widoków migawek:  
  
- [Raporty szczegóły migawki](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) przedstawiają typy i wystąpienia w jednej migawce.  
  
- [Raporty różnic migawek (diff)](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) porównują typy i wystąpienia w dwóch migawkach.  
  
  ![Linki widoku migawek](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  Numerowane elementy na zdjęciu widoku migawki to linki, które otwierają widoki raportów użycie pamięci.  
  
|Obraz|Opis|  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Tekst linku pokazuje łączną liczbę bajtów w pamięci podczas wykonywania migawki.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki, który jest posortowany według łącznego rozmiaru wystąpień typu.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Tekst linku pokazuje łączną liczbę obiektów w pamięci podczas wykonywania migawki.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki, który jest posortowany według liczby wystąpień typów.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Tekst linku pokazuje różnicę między łącznym rozmiarem obiektów w pamięci w momencie tej migawki i łącznym rozmiarem poprzedniej migawki.<br /><br /> Tekst linku jest liczbą dodatnią, gdy rozmiar pamięci tej migawki przekracza poprzednią wartość, a liczba ujemna, gdy rozmiar jest mniejszy. **Linia bazowa** tekstu linku wskazuje, że ta migawka jest pierwszą w sesji diagnostycznej; **Żadna różnica nie** wskazuje, że różnica wynosi zero.<br /><br /> Wybierz ten link, aby wyświetlić raport różnic migawek, który jest posortowany według różnicy w łącznym rozmiarze wystąpień typów.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Tekst linku pokazuje różnicę między łączną liczbą obiektów pamięci w tej migawce i liczbą obiektów w poprzedniej migawce.<br /><br /> Wybierz ten link, aby wyświetlić raport różnic migawek, który jest posortowany według różnicy w łącznej liczbie wystąpień typów.|  
  
## <a name="snapshot-reports"></a><a name="BKMK_Snapshot_reports"></a> Raporty migawek  
 ![Raport migawek użycia pamięci](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
### <a name="snapshot-report-trees"></a><a name="BKMK_Snapshot_report_trees"></a> Drzewa raportów migawek  
  
#### <a name="managed-heap"></a><a name="BKMK_Managed_Heap"></a> Sterta zarządzana  
 Zarządzane drzewo sterty zarządzane drzewo sterty [(szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) i [zarządzane drzewo sterty (porównanie migawek)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) pokazują typy i wystąpienia w raporcie. Wybranie typu lub wystąpienia powoduje wyświetlenie **ścieżek do katalogu głównego** i **przywoływanych obiektów** drzewa dla wybranego elementu.  
  
#### <a name="paths-to-root"></a><a name="BKMK_Paths_to_Root"></a> Ścieżki do katalogu głównego  
 [Ścieżki do drzewa głównego (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) i [ścieżki do drzewa głównego (porównanie migawek)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) pokazują łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł wyrzucania elementów bezużytecznych czyści pamięć dla obiektu tylko wtedy .NET Framework, gdy wszystkie odwołania do niego zostały wydane.  
  
#### <a name="referenced-objects"></a><a name="BKMK_Referenced_Objects"></a> Przywoływane obiekty  
 [Drzewo przywoływanych obiektów (szczegóły migawki)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) i [drzewo obiektów, do których się odwołuje (porównanie migawek)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) , pokazują obiekty, do których odwołuje się wybrany typ lub wystąpienie.  
  
### <a name="object-type-and-instance-fields"></a><a name="BKMK_Object_Type_and_Instance_fields"></a> Typ obiektu i pola wystąpienia  
 Gdy wpis **typu obiektu** ma wpisy podrzędne, możesz wybrać ikonę strzałki, aby je wyświetlić. Jeśli kolor tekstu **typu obiektu** jest niebieski, możesz wybrać go, aby przejść do obiektu w jego pliku kodu źródłowego. Plik źródłowy zostanie otwarty w osobnym oknie.  
  
 Nazwy wystąpień to unikatowe identyfikatory, które są generowane przez narzędzie użycie pamięci.  
  
 Jeśli zauważysz typ, którego nie można łatwo zidentyfikować, lub jeśli nie wiesz, jak to się dzieje w kodzie, prawdopodobnie obiekt z .NET Framework, systemu operacyjnego lub kompilatora, który jest wyświetlany przez narzędzie użycie pamięci, ponieważ jest uwzględniany w łańcuchach własności obiektów.  
  
### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a> Filtry drzewa raportów  
 Większość aplikacji zawiera Surprisingly dużą liczbę typów, z których większość nie jest interesująca dla deweloperów aplikacji. Narzędzie **użycie pamięci** definiuje dwa filtry, których można użyć do ukrycia większości z tych typów w **zarządzanym stosie** i **ścieżkach do drzew głównych** . Można również filtrować drzewo według nazwy typu.  
  
 ![Opcje sortowania i filtrowania](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
#### <a name="filter"></a><a name="BKMK_Filter"></a> Filtru  
 Wprowadź ciąg w polu **Filtr** , aby ograniczyć wyświetlanie drzewa do typów zawierających określony tekst. W filtrze nie jest rozróżniana wielkość liter i rozpoznaje określony ciąg w dowolnej części nazw typów.  
  
#### <a name="collapse-small-objects"></a><a name="BKMK_Collapse_Small_Objects"></a> Zwiń małe obiekty  
 Gdy ten filtr jest stosowany, typy, których **rozmiar (w bajtach)** jest mniejszy niż 0,5 procent całkowitego rozmiaru pamięci migawek, są ukryte na liście **sterty zarządzane** .  
  
#### <a name="just-my-code"></a><a name="BKMK_Just_My_Code"></a> Tylko mój kod  
 Filtr **tylko mój kod** ukrywa większość wystąpień generowanych przez kod zewnętrzny. Typy zewnętrzne są własnością systemu operacyjnego lub składników struktury lub są generowane przez kompilator.  
  
## <a name="snapshot-details-reports"></a><a name="BKMK_Snapshot_details_reports"></a> Raporty szczegółów migawek  
 Raport szczegóły migawki służy do skoncentrowania się na jednej migawce z sesji diagnostycznej. Aby otworzyć raport szczegóły, wybierz jedno z łączy w widoku migawki, jak pokazano na poniższej ilustracji. Oba linki otwierają ten sam raport; Jedyną różnicą jest początkowa kolejność sortowania **zarządzanego drzewa sterty** w raporcie. W obu przypadkach można zmienić kolejność sortowania po otwarciu raportu.  
  
 ![Linki do raportu migawek w widoku migawki](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
- Link **MB** sortuje raport według kolumny **rozmiar włącznie (w bajtach)** .  
  
- Link **obiekty** sortuje raport według kolumny **Count** .  
  
### <a name="managed-heap-tree-snapshot-details"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Zarządzane drzewo sterty (szczegóły migawki)  
 W drzewie **zarządzanym sterty** są wyświetlane typy obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić dziesięć największych wystąpień typu, posortowane według rozmiaru. Wybranie typu lub wystąpienia powoduje wyświetlenie **ścieżek do katalogu głównego** i **przywoływanych obiektów** drzewa dla wybranego elementu.  
  
 ![Zarządzane drzewo sterty](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|Nazwa|Opis|  
|-|-|  
|**Typ obiektu**|Nazwa typu lub wystąpienia obiektu.|  
|**Liczbą**|Liczba wystąpień obiektów typu. Liczba jest zawsze 1 dla wystąpienia.|  
|**Rozmiar (w bajtach)**|Dla typu, rozmiar wszystkich wystąpień typu w migawce pamięci, z wyłączeniem rozmiaru obiektów zawartych w wystąpieniach.<br /><br /> Dla wystąpienia, wpisz, rozmiar obiektu, z wyłączeniem rozmiaru obiektów zawartych w wystąpieniu. Liczba.|  
|**Rozmiar włącznie (w bajtach)**|Rozmiar wystąpień typu lub rozmiar pojedynczego wystąpienia, łącznie z rozmiarem zawartych obiektów.|  
  
### <a name="paths-to-root-tree-snapshot-details"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Ścieżki do drzewa głównego (szczegóły migawki)  
 **Ścieżka do drzewa głównego** pokazuje łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł wyrzucania elementów bezużytecznych czyści pamięć dla obiektu tylko wtedy .NET Framework, gdy wszystkie odwołania do niego zostały wydane.  
  
 ![Ścieżki do drzewa głównego dla typów](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Po wyświetleniu typu w drzewie **ścieżki do katalogu głównego** liczba obiektów typów, które zawierają odwołania do tego typu, jest wyświetlana w kolumnie **liczba odwołań** . Ta kolumna nie jest wyświetlana podczas analizowania wystąpienia.  
  
### <a name="referenced-objects-tree-snapshot-details"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Drzewo przywoływanych obiektów (szczegóły migawki)  
 Drzewo **obiektów, do których się odwołuje** , pokazuje obiekty, do których odwołuje się wybrany typ lub wystąpienie.  
  
 ![Przywoływane drzewo Objjects dla wystąpień](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|Nazwa|Opis|  
|-|-|  
|**Typ/wystąpienie obiektu**|Nazwa typu lub wystąpienia obiektu.|  
|**Rozmiar (w bajtach)**|Dla typu, rozmiar wszystkich wystąpień typu, z wyłączeniem rozmiaru obiektów zawartych w typie.<br /><br /> Dla wystąpienia, rozmiar obiektu, z wyłączeniem rozmiaru obiektów zawartych w obiekcie.|  
|**Rozmiar włącznie (w bajtach)**|Łączny rozmiar wystąpień typu lub rozmiaru wystąpienia, łącznie z rozmiarem zawartych obiektów.|  
  
## <a name="snapshot-difference-diff-reports"></a><a name="BKMK_Snapshot_difference__diff__reports"></a> Raporty różnic migawek (diff)  
 Raport różnica migawek (diff) przedstawia zmiany między migawką podstawową a migawką, która została wykonana bezpośrednio przed nią. Aby otworzyć raport diff, wybierz jedno z linków w widoku migawki, jak pokazano na poniższej ilustracji. Oba linki otwierają ten sam raport; Jedyną różnicą jest początkowa kolejność sortowania **zarządzanego drzewa sterty** w raporcie. Kolejność sortowania można zmienić po otwarciu raportu.  
  
 ![Linki do raportu różnic w widoku migawki](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
- Link **MB** sortuje raport według kolumny **rozmiar włącznie (w bajtach)** .  
  
- Link **obiekty** sortuje raport według kolumny **Count** .  
  
### <a name="managed-heap-tree-snapshot-diff"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Zarządzane drzewo sterty (porównanie migawek)  
 W drzewie **zarządzanym sterty** są wyświetlane typy obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić dziesięć największych wystąpień typu, posortowane według rozmiaru. Wybranie typu lub wystąpienia powoduje wyświetlenie **ścieżek do katalogu głównego** i **przywoływanych obiektów** drzewa dla wybranego elementu.  
  
 ![Zarządzane drzewo sterty dla typu w raporcie różnicowym](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Zauważ, że kolumny **Liczba**, **rozmiar (bajty)** i **rozmiar włącznie (w bajtach)** zostały zwinięte na obrazie.  
  
|Nazwa|Opis|  
|-|-|  
|**Typ obiektu**|Nazwa typu lub wystąpienia obiektu.|  
|**Liczbą**|Liczba wystąpień typu w podstawowej migawce. **Liczba** jest zawsze 1 dla wystąpienia.|  
|**Różnica w liczbie**|Dla typu, różnica w liczbie wystąpień typu między migawką podstawową i poprzednią migawką. Pole jest puste dla wystąpienia.|  
|**Rozmiar (w bajtach)**|Rozmiar obiektów w podstawowej migawce, z wyłączeniem rozmiaru obiektów zawartych w obiektach. Dla typu, **rozmiar (w bajtach)** i **rozmiar włącznie (w bajtach)** są sumami rozmiarów wystąpień typu.|  
|**Różnica w łącznym rozmiarze (w bajtach)**|Dla typu, różnica w łącznym rozmiarze wystąpień typu między migawką podstawową i poprzednią, z wyłączeniem rozmiaru obiektów zawartych w wystąpieniach. Pole jest puste dla wystąpienia.|  
|**Rozmiar włącznie (w bajtach)**|Rozmiar obiektów w podstawowej migawce, łącznie z rozmiarem obiektów zawartych w obiektach.|  
|**Różnica w rozmiarze włącznie (w bajtach)**|Dla typu, różnica w rozmiarze wszystkich wystąpień typu między migawką podstawową i poprzednią migawką, włącznie z rozmiarem obiektów zawartych w obiektach. Pole jest puste dla wystąpienia.|  
  
### <a name="paths-to-root-tree-snapshot-diff"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Ścieżki do drzewa głównego (porównanie migawek)  
 **Ścieżka do drzewa głównego** pokazuje łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł wyrzucania elementów bezużytecznych czyści pamięć dla obiektu tylko wtedy .NET Framework, gdy wszystkie odwołania do niego zostały wydane.  
  
 ![Ścieżki do drzewa głównego dla wystąpień w widoku różnicowym](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
### <a name="referenced-objects-tree-snapshot-diff"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Drzewo obiektów, do których istnieją odwołania (porównanie migawek)  
 Drzewo **obiektów, do których się odwołuje** , pokazuje obiekty, których typ podstawowy lub odwołanie do wystąpienia.  
  
 ![Przywoływane drzewo Objjects dla wystąpień](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|Nazwa|Opis|  
|-|-|  
|**Typ/wystąpienie obiektu**|Nazwa typu lub wystąpienia obiektu.|  
|**Rozmiar (w bajtach)**|Dla wystąpienia, rozmiar obiektu w podstawowej migawce, z wyłączeniem rozmiaru obiektów zawartych w wystąpieniu.<br /><br /> Dla typu, łączny rozmiar wystąpień typu w podstawowej migawce, z wyłączeniem rozmiaru obiektów zawartych w wystąpieniu.|  
|**Rozmiar włącznie (w bajtach)**|Rozmiar obiektów w podstawowej migawce, łącznie z rozmiarem obiektów zawartych w obiektach.|  
  
## <a name="see-also"></a>Zobacz też  
 [Pamięć JavaScript](../profiling/javascript-memory.md)   
 [Analizowanie wydajności aplikacji](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)   
 [Uruchom narzędzia do oceny wydajności i diagnostyki](https://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [Najlepsze rozwiązania w zakresie wydajności dla aplikacji ze sklepu Windows przy użyciu języków C++, C# i Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Diagnozowanie problemów z pamięcią za pomocą nowego narzędzia użycie pamięci w programie Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)
