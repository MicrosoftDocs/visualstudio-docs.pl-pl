---
title: Analizowanie użycia pamięci w profilerze wydajności
description: Dowiedz się, jak używać narzędzia użycie pamięci bez debugera w profilerze wydajności programu Visual Studio, aby monitorować użycie pamięci przez aplikację.
ms.custom: ''
ms.date: 04/02/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c81bcb029499b77b2f5b25c598437f1fcbf70854
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886162"
---
# <a name="analyze-memory-usage-without-debugging-in-the-performance-profiler"></a>Analizowanie użycia pamięci bez debugowania w profilerze wydajności

Narzędzie **użycie pamięci** monitoruje użycie pamięci przez aplikację. Za pomocą tego narzędzia można analizować efekty związane z pamięcią w czasie rzeczywistym scenariuszy, które aktywnie opracowujesz w programie Visual Studio. Można utworzyć szczegółowe migawki Stanów pamięci aplikacji i porównać migawki w celu znalezienia głównych przyczyn problemów z pamięcią. Narzędzie użycie pamięci jest obsługiwane w aplikacjach w trybie .NET, ASP.NET, C++ lub mieszanym (.NET i Native).

Narzędzie użycie pamięci można uruchomić [z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). W tym artykule pokazano, jak używać narzędzia użycie pamięci bez debugera w **profilerze wydajności** programu Visual Studio, który jest zalecany w przypadku kompilacji wydania.

## <a name="memory-usage-diagnostic-sessions"></a>Sesje diagnostyczne dotyczące użycia pamięci

**Aby rozpocząć sesję diagnostyczną wykorzystania pamięci:**

1. Otwórz projekt w programie Visual Studio.

   Narzędzie użycie pamięci obsługuje aplikacje platformy .NET, ASP.NET, C++ lub mieszane (.NET i Native).

1. W menu Debuguj Ustaw konfigurację rozwiązania na **Zwolnij** i wybierz pozycję **lokalny debuger systemu Windows** (lub **komputer lokalny**) jako cel wdrożenia.

1. Na pasku menu wybierz kolejno opcje **Debuguj program**  >  **Profiler wydajności**.

1. W obszarze **dostępne narzędzia** wybierz pozycję **użycie pamięci**, a następnie wybierz pozycję **Uruchom**.

   ![Rozpocznij sesję diagnostyczną wykorzystania pamięci](../profiling/media/memuse_start_diagnosticssession.png "Rozpocznij sesję diagnostyczną wykorzystania pamięci")

### <a name="monitor-memory-use"></a>Monitoruj użycie pamięci

Po uruchomieniu sesji diagnostycznej aplikacja zostanie uruchomiona, a w oknie **Narzędzia diagnostyczne** zostanie wyświetlony wykres osi czasu aplikacji.

![Zrzut ekranu okna narzędzia diagnostyczne w programie Visual Studio Performance Profiler przedstawiający wykres osi czasu aplikacji.](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Wykres osi czasu przedstawia fluktuacje pamięci podczas uruchamiania aplikacji. Skoki na wykresie zwykle wskazują, że jakiś kod zbiera lub tworzy dane, a następnie odrzuca je po zakończeniu przetwarzania. Duże skoki wskazują obszary, które mogą być optymalizowane. Większym problemem jest wzrost zużycia pamięci, który nie jest zwracany, ponieważ może to wskazywać na niewydajne użycie pamięci lub nawet przeciek pamięci.

### <a name="take-snapshots-of-app-memory-states"></a>Wykonaj migawki Stanów pamięci aplikacji

Aplikacja używa dużej liczby obiektów i może chcieć skupić analizę w jednym scenariuszu. Możesz też znaleźć problemy z pamięcią, aby zbadać. Podczas sesji diagnostycznej można wykonać migawki w celu przechwycenia użycia pamięci w określonych momentach. Dobrym pomysłem jest uzyskanie podstawowej migawki aplikacji, zanim pojawi się problem z pamięcią, kolejną migawką po pierwszym wystąpieniu problemu i dodatkowych migawek, jeśli można powtórzyć ten scenariusz.

Aby zebrać migawki, wybierz pozycję **zrób migawkę** , jeśli chcesz przechwytywać dane pamięci.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a> Zamknij sesję diagnostyczną

Aby zatrzymać sesję monitorowania bez tworzenia raportu, po prostu Zamknij okno diagnostyki. Aby wygenerować raport po zakończeniu zbierania lub tworzenia migawek, wybierz pozycję **Zatrzymaj zbieranie**.

![Zatrzymaj zbieranie](../profiling/media/memuse__stopcollection.png "Zatrzymaj zbieranie")

## <a name="memory-usage-reports"></a>Raporty użycia pamięci

Po zatrzymaniu zbierania danych narzędzie **użycie pamięci** zatrzyma aplikację i wyświetli stronę przegląd **użycia pamięci** .

![Zrzut ekranu strony przegląd w narzędziu Użycie pamięci w profilerze wydajności programu Visual Studio, który pokazuje wykres użycia pamięci i dwa okienka migawek.](../profiling/media/memuse__reportoverview1.png "Strona przegląd użycia pamięci")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> Migawki użycia pamięci

Liczby w okienkach **migawek** pokazują bajty i obiekty w pamięci, gdy każda migawka została wykonana, i różnicę między migawką a poprzednią.

Liczby to linki, które otwierają szczegółowe widoki raportów **użycia pamięci** w nowych oknach programu Visual Studio. [Raport szczegóły migawki](#snapshot-details-reports) przedstawia typy i wystąpienia w jednej migawce. [Raport różnica migawek (diff)](#snapshot-difference-diff-reports) porównuje typy i wystąpienia w dwóch migawkach.

  ![Linki widoku migawek](../profiling/media/memuse__snapshotview_numbered.png "Linki widoku migawek")

|Image (Obraz)|Opis|
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Całkowita liczba bajtów w pamięci podczas tworzenia migawki.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegółów migawek posortowany według łącznego rozmiaru wystąpień typu.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Całkowita liczba obiektów w pamięci podczas tworzenia migawki.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegółów migawek posortowany według liczby wystąpień typów.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Różnica między całkowitym rozmiarem obiektów pamięci w tej migawce i poprzednią migawką. <br /><br /> Liczba dodatnia oznacza, że rozmiar pamięci tej migawki jest większy niż poprzednia, a liczba ujemna oznacza, że rozmiar jest mniejszy. **Linia bazowa** oznacza, że migawka jest pierwszą w sesji diagnostycznej. **Żadna różnica nie** oznacza, że różnica wynosi zero.<br /><br /> Wybierz ten link, aby wyświetlić raport różnic migawek posortowany według różnicy w łącznym rozmiarze wystąpień typów.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Różnica między łączną liczbą obiektów pamięci w tej migawce i poprzednią migawką.<br /><br /> Wybierz ten link, aby wyświetlić raport różnic migawek posortowany według różnicy w łącznej liczbie wystąpień typów.|

## <a name="memory-usage-snapshot-reports"></a>Raporty dotyczące migawek użycia pamięci

<a name="BKMK_Snapshot_report_trees"></a> Po wybraniu jednego z linków migawek na stronie Przegląd **użycia pamięci** zostanie otwarty raport migawki na nowej stronie.

![Raport migawek użycia pamięci](../profiling/media/memuse_snapshotreport_all.png "Raport migawek użycia pamięci")

W raporcie migawki można rozwinąć wpisy **typu obiektu** w celu wyświetlenia wpisów podrzędnych. Nazwy wystąpień to unikatowe identyfikatory, które są generowane przez narzędzie użycie pamięci.

Jeśli **Typ obiektu** to niebieska, możesz go zaznaczyć, aby przejść do obiektu w kodzie źródłowym w osobnym oknie.

Typy, których nie można zidentyfikować lub których zaangażowanie w kodzie nie jest zrozumiałe, prawdopodobnie .NET, system operacyjny lub obiekty kompilatora. Narzędzie **użycie pamięci** wyświetla te obiekty, jeśli są one wykorzystywane w łańcuchach własności obiektów.

W raporcie migawki:

- **Zarządzane drzewo sterty** pokazuje typy i wystąpienia w raporcie. Wybranie typu lub wystąpienia powoduje wyświetlenie **ścieżek do katalogu głównego** i **przywoływanych obiektów** drzewa dla wybranego elementu.

- **Ścieżka do drzewa głównego** pokazuje łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł wyrzucania elementów bezużytecznych platformy .NET czyści pamięć dla obiektu tylko wtedy, gdy wszystkie odwołania do niego zostały wydane.

- **Przywoływane typy** lub drzewa **obiektów, do** których istnieją odwołania, są wyświetlane obiekty, do których odwołuje się wybrany typ lub wystąpienie.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a> Filtry drzewa raportów

Wiele typów w aplikacjach nie jest bardzo interesujące dla deweloperów aplikacji. Filtry migawek można ukryć większość z tych typów w **zarządzanym stosie** i **ścieżkach do drzew głównych** .

![Opcje sortowania i filtrowania](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a> Aby odfiltrować drzewo według nazwy typu, wprowadź nazwę w polu **Filtr** . W filtrze nie ma wielkości liter i rozpoznaje określony ciąg w dowolnej części nazwy typu.

- <a name="BKMK_Collapse_Small_Objects"></a> Wybierz pozycję **Zwiń małe obiekty** na liście rozwijanej **Filtr** , aby ukryć typy, których **rozmiar (w bajtach)** jest mniejszy niż 0,5 procent całkowitej ilości pamięci.

- <a name="BKMK_Just_My_Code"></a> Wybierz pozycję **tylko mój kod** na liście rozwijanej **Filtr** , aby ukryć większość wystąpień generowanych przez kod zewnętrzny. Typy zewnętrzne należą do systemu operacyjnego lub składników struktury lub są generowane przez kompilator.

## <a name="snapshot-details-reports"></a>Raporty szczegółów migawek

 Raport szczegóły migawki zawiera opis jednej migawki z sesji diagnostycznej. Aby otworzyć raport, wybierz link rozmiar lub obiekty w okienku migawki.

 ![Linki do raportu migawek w okienku migawek](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Linki do raportu migawek w okienku migawek")

Oba linki otwierają ten sam raport. Jedyną różnicą jest początkowa kolejność sortowania drzewa **sterty zarządzanej** . Link size sortuje raport według kolumny **size (bajty)** . Link obiekty sortuje raport według kolumny **Count** . Można zmienić kolumnę sortowania lub kolejność po otwarciu raportu.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Zarządzane drzewo sterty (raporty szczegółów migawek)
 W drzewie **zarządzanym sterty** są wyświetlane typy obiektów, które są przechowywane w pamięci. Rozwiń nazwę typu, aby wyświetlić dziesięć największych wystąpień typu, posortowane według rozmiaru. Wybierz typ lub wystąpienie, aby wyświetlić **ścieżki do katalogu głównego** i **przywoływanych obiektów** drzewa dla wybranego elementu.

 ![Zarządzane drzewo sterty](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Zarządzane drzewo sterty")

**Zarządzane drzewo sterty** w raporcie ze szczegółowymi informacjami o migawce zawiera następujące kolumny:

|Nazwa|Opis|
|-|-|
|**Typ obiektu**|Nazwa typu lub wystąpienia obiektu.|
|**Liczbą**|Liczba wystąpień obiektów typu. **Liczba**  jest zawsze 1 dla wystąpienia.|
|**Rozmiar (w bajtach)**|Dla typu, rozmiar wszystkich wystąpień typu w migawce, mniejszy rozmiar obiektów zawartych w wystąpieniach.<br /><br /> Dla wystąpienia, rozmiar obiektu, mniejszy od rozmiaru obiektów zawartych w wystąpieniu. |
|**Rozmiar włącznie (w bajtach)**|Rozmiar wystąpień typu lub rozmiar pojedynczego wystąpienia, łącznie z rozmiarem zawartych obiektów.|
|**Moduł**|Moduł, który zawiera obiekt.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Ścieżki do drzewa głównego (raporty ze szczegółowymi informacjami o migawce)
**Ścieżka do drzewa głównego** pokazuje łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł wyrzucania elementów bezużytecznych platformy .NET czyści pamięć dla obiektu tylko wtedy, gdy wszystkie odwołania do niego zostały wydane.

Dla typu w drzewie **ścieżki do katalogu głównego** liczba obiektów, które zawierają odwołania do tego typu, pojawia się w kolumnie **liczba odwołań** .

![Ścieżki do drzewa głównego dla typów](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Ścieżki do drzewa głównego dla typów")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Przywoływane typy lub drzewo przywoływanych obiektów (raporty szczegółów migawek)
**Przywoływane typy** lub drzewa **obiektów, do** których istnieją odwołania, są wyświetlane obiekty, do których odwołuje się wybrany typ lub wystąpienie.

![Drzewo przywoływanych obiektów dla wystąpień](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Drzewo przywoływanych obiektów dla wystąpień")

Drzewo **typów, do których istnieją odwołania** w raporcie szczegóły migawki, zawiera następujące kolumny. Drzewo **obiektów, do którego się odwoływano** , nie ma kolumny **Count Reference** .

|Nazwa|Opis|
|-|-|
|**Typ obiektu** lub **wystąpienie**|Nazwa typu lub wystąpienia.|
|**Liczba odwołań**|Dla typów, liczba wystąpień obiektów typu.|
|**Rozmiar (w bajtach)**|Dla typu, rozmiar wszystkich wystąpień typu, mniejszy rozmiar obiektów zawartych w typie.<br /><br /> Dla wystąpienia, rozmiar obiektu, mniejszy od rozmiaru obiektów zawartych w obiekcie.|
|**Rozmiar włącznie (w bajtach)**|Łączny rozmiar wystąpień typu lub rozmiar wystąpienia, łącznie z rozmiarem zawartych obiektów.|
|**Moduł**|Moduł, który zawiera obiekt.|

## <a name="snapshot-difference-diff-reports"></a>Raporty różnic migawek (diff)

Raport różnica migawek (diff) przedstawia zmiany między migawką podstawową i poprzednią migawką. Aby otworzyć raport diff, wybierz jedno z łączy różnic w okienku migawki.

Oba linki otwierają ten sam raport. Jedyną różnicą jest początkowa kolejność sortowania **zarządzanego drzewa sterty** w raporcie. Link size sortuje raport według kolumny **różnicowego rozmiaru (w bajtach)** . Łącze obiekty sortuje raport według kolumny **Liczba różnic** . Można zmienić kolumnę sortowania lub kolejność po otwarciu raportu.

 ![Łącze do raportu różnic w okienku migawki](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Łącze do raportu różnic w okienku migawki")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Zarządzane drzewo sterty (raporty różnic migawek)

 W drzewie **zarządzanym sterty** są wyświetlane typy obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić dziesięć największych wystąpień typu, posortowane według rozmiaru. Wybierz typ lub wystąpienie, aby wyświetlić **ścieżki do katalogu głównego** i **przywoływanych obiektów** drzewa dla wybranego elementu.

 ![Zarządzane drzewo sterty dla typu w raporcie różnicowym](../profiling/media/memuse_snapshotdiff_type_heap.png "Zarządzane drzewo sterty dla typu w raporcie różnicowym")

**Zarządzane drzewo sterty** w raporcie różnic migawek zawiera następujące kolumny:

|Nazwa|Opis|
|-|-|
|**Typ obiektu**|Nazwa typu lub wystąpienia obiektu.|
|**Liczbą**|Liczba wystąpień typu w podstawowej migawce. **Liczba** jest zawsze 1 dla wystąpienia.|
|**Różnica w liczbie**|Dla typu, różnica w liczbie wystąpień typu między migawką podstawową i poprzednią migawką. Pole jest puste dla wystąpienia.|
|**Rozmiar (w bajtach)**|Rozmiar obiektów w podstawowej migawce, mniejszej niż rozmiar obiektów w obiektach. Dla typu, **rozmiar (w bajtach)** i **rozmiar włącznie (w bajtach)** są sumami rozmiarów wystąpień typu.|
|**Różnica w łącznym rozmiarze (w bajtach)**|Dla typu, różnica w łącznym rozmiarze wystąpień typu między migawką podstawową i poprzednią, mniejszą od rozmiaru obiektów w wystąpieniach. Pole jest puste dla wystąpienia.|
|**Rozmiar włącznie (w bajtach)**|Rozmiar obiektów w podstawowej migawce, łącznie z rozmiarem obiektów w obiektach.|
|**Różnica w rozmiarze włącznie (w bajtach)**|Dla typu, różnica w rozmiarze wszystkich wystąpień typu między migawką podstawową i poprzednią migawką, włącznie z rozmiarem obiektów w obiektach. Pole jest puste dla wystąpienia.|
|**Moduł**|Moduł, który zawiera obiekt.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Ścieżki do drzewa głównego (raporty różnic migawek)

**Ścieżka do drzewa głównego** pokazuje łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł wyrzucania elementów bezużytecznych platformy .NET czyści pamięć dla obiektu tylko wtedy, gdy wszystkie odwołania do niego zostały wydane.

Dla typu w drzewie **ścieżki do katalogu głównego** liczba obiektów, które zawierają odwołania do tego typu, pojawia się w kolumnie **liczba odwołań** . Różnica w liczniku od poprzedniej migawki znajduje się w kolumnie **różnic odwołania** .

 ![Ścieżki do drzewa głównego w raporcie różnicowym](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Ścieżki do drzewa głównego w raporcie różnicowym")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Przywoływane typy lub drzewo przywoływanych obiektów (raporty różnic migawek)

**Przywoływane typy** lub drzewa **obiektów, do** których istnieją odwołania, są wyświetlane obiekty, do których odwołuje się wybrany typ lub wystąpienie.

![Przywoływane typy w raporcie różnicowym](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Przywoływane typy w raporcie różnicowym")

Drzewo **typów, do których istnieją odwołania** w raporcie różnic migawek, zawiera następujące kolumny. Drzewo **przywoływanych obiektów** ma **wystąpienie**, **rozmiar (bajty)**, **rozmiar włącznie (w bajtach)** i kolumny **modułów** .

|Nazwa|Opis|
|-|-|
|**Typ obiektu** lub **wystąpienie**|Nazwa typu lub wystąpienia obiektu.|
|**Liczba odwołań**|Liczba wystąpień typu w podstawowej migawce.|
|**Różnica w liczbie odwołań**|Dla typu, różnica w liczbie wystąpień typu między migawką podstawową i poprzednią migawką.|
|**Rozmiar (w bajtach)**|Rozmiar obiektów w podstawowej migawce, mniejszej niż rozmiar obiektów w obiektach. Dla typu, **rozmiar (w bajtach)** i **rozmiar włącznie (w bajtach)** są sumami rozmiarów wystąpień typu.|
|**Różnica w łącznym rozmiarze (w bajtach)**|Dla typu, różnica w łącznym rozmiarze wystąpień typu między migawką podstawową i poprzednią, mniejszą od rozmiaru obiektów w wystąpieniach. |
|**Rozmiar włącznie (w bajtach)**|Rozmiar obiektów w podstawowej migawce, łącznie z rozmiarem obiektów w obiektach.|
|**Różnica w rozmiarze włącznie (w bajtach)**|Dla typu, różnica w rozmiarze wszystkich wystąpień typu między migawką podstawową i poprzednią migawką, włącznie z rozmiarem obiektów w obiektach.|
|**Moduł**|Moduł, który zawiera obiekt.|

## <a name="see-also"></a>Zobacz też
- [Pamięć JavaScript](../profiling/javascript-memory.md)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
- [Najlepsze rozwiązania w zakresie wydajności dla aplikacji platformy UWP przy użyciu języków C++, C# i Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Diagnozowanie problemów z pamięcią za pomocą nowego narzędzia użycie pamięci w programie Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)