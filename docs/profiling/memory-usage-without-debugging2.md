---
title: Analizowanie użycia pamięci bez debugowania | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 04/02/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5af369669245bca9c5de74566dd8594164acf8bb
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638829"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Analizowanie użycia pamięci bez debugera

Narzędzie **Użycie pamięci** monitoruje użycie pamięci aplikacji. Za pomocą narzędzia można zbadać efekty pamięci w czasie rzeczywistym scenariuszy, które aktywnie tworzysz w programie Visual Studio. Można zrobić szczegółowe migawki stanów pamięci aplikacji i porównać migawki, aby znaleźć główne przyczyny problemów z pamięcią.

Narzędzie **Użycie pamięci** można uruchomić z [debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md). W tym artykule pokazujemy, jak używać narzędzia **Użycie pamięci** bez debugera w programie Visual Studio **Performance Profiler**.

## <a name="memory-usage-diagnostic-sessions"></a>Sesje diagnostyczne użycia pamięci

**Aby rozpocząć sesję diagnostyczną użycia pamięci:**

1. Otwórz projekt w programie Visual Studio.

   Narzędzie Użycie pamięci obsługuje aplikacje .NET, ASP.NET, natywne lub mieszane (NET i natywne).

1. W menu Debugowanie ustaw konfigurację rozwiązania na **Zwolnij** i wybierz **opcję Lokalny debuger systemu Windows** (lub Komputer **lokalny)** jako miejsce docelowe wdrożenia.

1. Na pasku menu wybierz pozycję **Debug** > **Performance Profiler**.

1. W obszarze **Dostępne narzędzia**wybierz pozycję **Użycie pamięci**, a następnie wybierz pozycję **Start**.

   ![Uruchamianie sesji diagnostycznej użycia pamięci](../profiling/media/memuse_start_diagnosticssession.png "Uruchamianie sesji diagnostycznej użycia pamięci")

### <a name="monitor-memory-use"></a>Monitorowanie wykorzystania pamięci

Po uruchomieniu sesji diagnostycznej aplikacja zostanie uruchomiony, a okno **Narzędzia diagnostyczne** wyświetli wykres osi czasu użycia pamięci aplikacji.

![Strona omówienie użycia pamięci](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Wykres osi czasu pokazuje wahania pamięci w miarę pracy aplikacji. Skoki na wykresie zwykle wskazują, że niektóre kod jest zbieranie lub tworzenie danych, a następnie odrzuca go po zakończeniu przetwarzania. Duże kolce wskazują obszary, które można zoptymalizować. Bardziej niepokojące jest wzrost zużycia pamięci, który nie jest zwracany, ponieważ może to wskazywać na nieefektywne użycie pamięci, a nawet przeciek pamięci.

### <a name="take-snapshots-of-app-memory-states"></a>Tworzenie migawek stanów pamięci aplikacji

Aplikacja używa dużej liczby obiektów i można skoncentrować analizę na jednym scenariuszu. Lub mogą wystąpić problemy z pamięcią do zbadania. Można robić migawki podczas sesji diagnostycznej, aby uchwycić użycie pamięci w określonych momentach. Warto uzyskać migawkę linii bazowej aplikacji przed pojawieniem się problemu z pamięcią, inną migawkę po pierwszym wystąpieniu problemu i dodatkowe migawki, jeśli można powtórzyć scenariusz.

Aby zbierać migawki, wybierz opcję **Zrób migawkę,** gdy chcesz przechwycić dane pamięci.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a>Zamykanie sesji diagnostycznej

Aby zatrzymać sesję monitorowania bez tworzenia raportu, po prostu zamknij okno diagnostyczne. Aby wygenerować raport po zakończeniu zbierania lub wykonaniu migawek, wybierz **opcję Zatrzymaj zbieranie**.

![Zatrzymaj kolekcję](../profiling/media/memuse__stopcollection.png "Zatrzymaj kolekcję")

## <a name="memory-usage-reports"></a>Raporty użycia pamięci

Po zatrzymaniu zbierania danych narzędzie **Użycie pamięci** zatrzymuje aplikację i wyświetla stronę omówienie **użycia pamięci.**

![Strona omówienie użycia pamięci](../profiling/media/memuse__reportoverview1.png "Strona omówienie użycia pamięci")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a>Migawki użycia pamięci

Liczby w **okienkach migawki** pokazują bajty i obiekty w pamięci podczas każdej migawki i różnicę między migawką a poprzednią.

Liczby są łączami, które otwierają szczegółowe widoki raportu **użycia pamięci** w nowych oknach programu Visual Studio. [Raport szczegółów migawki](#snapshot-details-reports) pokazuje typy i wystąpienia w jednej migawce. [Raport różnicy migawki (diff)](#snapshot-difference-diff-reports) porównuje typy i wystąpienia w dwóch migawek.

  ![Łącza widoku migawki](../profiling/media/memuse__snapshotview_numbered.png "Łącza widoku migawki")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Całkowita liczba bajtów w pamięci podczas migawki została podjęta.<br /><br /> Wybierz to łącze, aby wyświetlić raport szczegółów migawki posortowany według całkowitego rozmiaru wystąpień typu.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Całkowita liczba obiektów w pamięci podczas migawki została podjęta.<br /><br /> Wybierz to łącze, aby wyświetlić raport szczegółów migawki posortowany według liczby wystąpień typów.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Różnica między całkowity rozmiar obiektów pamięci w tej migawki i poprzedniej migawki. <br /><br /> Liczba dodatnia oznacza, że rozmiar pamięci tej migawki jest większy niż poprzedni, a liczba ujemna oznacza, że rozmiar jest mniejszy. **Linia bazowa** oznacza, że migawka jest pierwszą w sesji diagnostycznej. **Brak różnicy** oznacza, że różnica wynosi zero.<br /><br /> Wybierz to łącze, aby wyświetlić raport różnicy migawki posortowany według różnicy w całkowitym rozmiarze wystąpień typów.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Różnica między całkowitą liczbą obiektów pamięci w tej migawki i poprzedniej migawki.<br /><br /> Wybierz to łącze, aby wyświetlić raport różnicy migawki posortowany według różnicy w całkowitej liczbie wystąpień typów.|

## <a name="memory-usage-snapshot-reports"></a>Raporty migawki użycia pamięci

<a name="BKMK_Snapshot_report_trees"></a>Po wybraniu jednego z łączy migawki na stronie Przegląd **użycia pamięci** raport migawki zostanie otwarty na nowej stronie.

![Raport migawki użycie pamięci](../profiling/media/memuse_snapshotreport_all.png "Raport migawki użycie pamięci")

W raporcie migawki można rozwinąć wpisy **typu obiektu,** aby wyświetlić wpisy podrzędne. Nazwy wystąpień są unikatowymi identyfikatorami generowanymi przez narzędzie Użycie pamięci.

Jeśli **typ obiektu** jest niebieski, można go wybrać, aby przejść do obiektu w kodzie źródłowym, w osobnym oknie.

Typy, których nie można zidentyfikować lub których udział w kodzie, którego nie rozumiesz, to prawdopodobnie obiekty .NET, systemu operacyjnego lub kompilatora. **Narzędzie Użycie pamięci** wyświetla te obiekty, jeśli są one zaangażowane w łańcuchy własności obiektów.

W raporcie migawki:

- Drzewo **Zarządzane sterty** pokazuje typy i wystąpienia w raporcie. Wybranie typu lub wystąpienia powoduje wyświetlenie drzewa **Ścieżki do obiektów głównych** i obiektów **odniesienia** dla zaznaczonego elementu.

- Drzewa **Ścieżki do katalogu głównego** jest wyświetlany łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł odśmiecania pamięci .NET czyści pamięć dla obiektu tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.

- Drzewo **Typy przywołytalne** lub **Obiekty odniesienia** pokazuje obiekty, do których odwołuje się wybrany typ lub wystąpienie.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a>Filtry drzewa raportów

Wiele typów w aplikacjach nie są bardzo interesujące dla deweloperów aplikacji. Filtry raportu migawki można ukryć większość z tych typów w **zarządzanych sterty** i ścieżki do drzew **głównych.**

![Opcje sortowania i filtrowania](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a>Aby filtrować drzewo według nazwy typu, wprowadź nazwę w polu **Filtr.** W filtrze nie jest rozróżniana wielkość liter i rozpoznaje określony ciąg w dowolnej części nazwy typu.

- <a name="BKMK_Collapse_Small_Objects"></a>Wybierz **pozycję Zwiń małe obiekty** z listy rozwijanej **Filtr,** aby ukryć typy, których **rozmiar (bajty)** jest mniejszy niż 0,5 procent całkowitej pamięci.

- <a name="BKMK_Just_My_Code"></a>Wybierz **pozycję Tylko mój kod** w **rozwijaniu filtru,** aby ukryć większość wystąpień generowanych przez kod zewnętrzny. Typy zewnętrzne należą do systemu operacyjnego lub składników struktury lub są generowane przez kompilator.

## <a name="snapshot-details-reports"></a>Raporty szczegółów migawki

 Raport szczegółów migawki opisuje jedną migawkę z sesji diagnostycznej. Aby otworzyć raport, zaznacz łącze rozmiar lub obiekty w okienku migawki.

 ![Łącza do raportu migawki w okienku migawki](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Łącza do raportu migawki w okienku migawki")

Oba łącza otwierają ten sam raport. Jedyną różnicą jest kolejność początkowa sortowania drzewa **sterty zarządzanej.** Łącze rozmiar sortuje raport według kolumny **Rozmiar włącznie (Bajty).** Łącze obiektów sortuje raport według kolumny **Liczba.** Po otwarciu raportu można zmienić kolumnę sortowania lub kolejność.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Drzewo zarządzanego sterty (raporty szczegółów migawki)
 **Drzewo Zarządzane sterty** wyświetla listę typów obiektów, które są przechowywane w pamięci. Rozwiń nazwę typu, aby wyświetlić dziesięć największych wystąpień tego typu, posortowanych według rozmiaru. Wybierz typ lub **wystąpienie,** aby wyświetlić drzewa Ścieżki do obiektów głównych i **obiektów odniesienia** dla zaznaczonego elementu.

 ![Drzewo zarządzanego sterty](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Drzewo zarządzanego sterty")

**Drzewo zarządzanego sterty** w raporcie szczegółów migawki ma następujące kolumny:

|||
|-|-|
|**Typ obiektu**|Nazwa typu lub wystąpienia obiektu.|
|**Liczba**|Liczba wystąpień obiektu typu. **Liczba** jest zawsze 1 dla wystąpienia.|
|**Rozmiar (bajty)**|Dla typu rozmiar wszystkich wystąpień typu w migawce, pomniejszonej o rozmiar obiektów zawartych w wystąpieniach.<br /><br /> W przypadku wystąpienia rozmiar obiektu, pomniejszony o rozmiar obiektów zawartych w wystąpieniu. |
|**Rozmiar włącznie (bajty)**|Rozmiar wystąpień typu lub rozmiar pojedynczego wystąpienia, w tym rozmiar obiektów zawartych.|
|**Moduł**|Moduł, który zawiera obiekt.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Ścieżki do drzewa głównego (raporty szczegółów migawki)
**Drzewa Ścieżki do katalogu głównego** jest wyświetlany łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł odśmiecania pamięci .NET czyści pamięć dla obiektu tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.

Dla typu w **paths to root** drzewa, liczba obiektów, które posiadają odwołania do tego typu pojawia się w licznik **odwołań** kolumny.

![Ścieżki do drzewa głównego dla typów](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Ścieżki do drzewa głównego dla typów")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Typy, do których istnieje odwołanie lub drzewo obiekty odniesienia (raporty szczegółów migawki)
Drzewo **Typy przywołytalne** lub **Obiekty odniesienia** pokazuje obiekty, do których odwołuje się wybrany typ lub wystąpienie.

![Drzewo obiektów, do których istnieje odwołanie, w przypadku wystąpień](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Drzewo obiektów, do których istnieje odwołanie, w przypadku wystąpień")

Drzewo **typy, do których istnieje odwołanie,** w raporcie szczegółów migawki zawiera następujące kolumny. Drzewo **Obiekty, do których istnieje odwołanie,** nie ma kolumny **Liczba odwołań.**

|||
|-|-|
|**Typ obiektu** lub **wystąpienie**|Nazwa typu lub wystąpienia.|
|**Liczba odwołań**|Dla typów liczba wystąpień obiektu typu.|
|**Rozmiar (bajty)**|Dla typu rozmiar wszystkich wystąpień typu, pomniejszony o rozmiar obiektów zawartych w typie.<br /><br /> W przypadku wystąpienia rozmiar obiektu, pomniejszony o rozmiar obiektów zawartych w obiekcie.|
|**Rozmiar włącznie (bajty)**|Całkowity rozmiar wystąpień typu lub rozmiar wystąpienia, w tym rozmiar obiektów zawartych w nim.|
|**Moduł**|Moduł, który zawiera obiekt.|

## <a name="snapshot-difference-diff-reports"></a>Raporty różnicy migawek (różnice)

Raport różnicy migawki (diff) pokazuje zmiany między migawką podstawową a poprzednią migawką. Aby otworzyć raport różnicowy, wybierz jedno z łączy różnicy w okienku migawki.

Oba łącza otwierają ten sam raport. Jedyną różnicą jest początkowa kolejność sortowania drzewa **sterty zarządzanej** w raporcie. Łącze rozmiar sortuje raport według **włącznie rozmiar diff (bajty)** kolumny. Łącze obiektów sortuje raport według kolumny **Count Diff.** Po otwarciu raportu można zmienić kolumnę sortowania lub kolejność.

 ![Łącza do raportu różnicy w okienku migawki](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Łącza do raportu różnicy w okienku migawki")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Drzewo zarządzanego sterty (raporty różnicowe migawki)

 **Drzewo Zarządzane sterty** wyświetla listę typów obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić dziesięć największych wystąpień tego typu, posortowanych według rozmiaru. Wybierz typ lub **wystąpienie,** aby wyświetlić drzewa Ścieżki do obiektów głównych i **obiektów odniesienia** dla zaznaczonego elementu.

 ![Drzewo zarządzanego sterty dla raportu różnicy typu](../profiling/media/memuse_snapshotdiff_type_heap.png "Drzewo zarządzanego sterty dla raportu różnicy typu")

**Drzewo zarządzanego sterty** w raporcie różnicy migawki ma następujące kolumny:

|||
|-|-|
|**Typ obiektu**|Nazwa typu lub wystąpienia obiektu.|
|**Liczba**|Liczba wystąpień typu w migawce podstawowej. **Liczba** jest zawsze 1 dla wystąpienia.|
|**Zlicz dyfernek**|Dla typu różnica w liczbie wystąpień typu między migawki podstawowej i poprzedniej migawki. Pole jest puste dla wystąpienia.|
|**Rozmiar (bajty)**|Rozmiar obiektów w podstawowego migawki, mniej rozmiaru obiektów w obiektach. Dla typu **Size (Bajty)** i **Rozmiar włącznie (Bajty)** są sumy rozmiarów wystąpień typu.|
|**Całkowity rozmiar różnicy (bajtów)**|Dla typu różnica w całkowity rozmiar wystąpień typu między migawki podstawowej i poprzedniej migawki, pomniejszonej o rozmiar obiektów w wystąpieniach. Pole jest puste dla wystąpienia.|
|**Rozmiar włącznie (bajty)**|Rozmiar obiektów w podstawowego migawki, w tym rozmiar obiektów w obiektach.|
|**Różnice rozmiaru włącznie (bajty)**|Dla typu różnica w rozmiarze wszystkich wystąpień typu między migawki podstawowej i poprzedniej migawki, w tym rozmiar obiektów w obiektach. Pole jest puste dla wystąpienia.|
|**Moduł**|Moduł, który zawiera obiekt.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Ścieżki do drzewa głównego (raporty różnicowe migawki)

**Drzewa Ścieżki do katalogu głównego** jest wyświetlany łańcuch obiektów, które odwołują się do typu lub wystąpienia. Moduł odśmiecania pamięci .NET czyści pamięć dla obiektu tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.

Dla typu w **paths to root** drzewa, liczba obiektów, które posiadają odwołania do tego typu pojawia się w licznik **odwołań** kolumny. Różnica w liczbie od poprzedniej migawki znajduje się w kolumnie **Diff odwołania.**

 ![Ścieżki do drzewa głównego w raporcie różnicowym](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Ścieżki do drzewa głównego w raporcie różnicowym")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Typy, do których istnieje odwołanie lub drzewo obiekty odniesienia (raporty różnicowe migawki)

Drzewo **Typy przywołytalne** lub **Obiekty odniesienia** pokazuje obiekty, do których odwołuje się wybrany typ lub wystąpienie.

![Typy odniesienia w raporcie różnicowym](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Typy odniesienia w raporcie różnicowym")

A **Referenced Types** drzewa w raporcie różnicy migawki ma następujące kolumny. Drzewo **Obiekty, do których istnieje odwołanie,** zawiera kolumny **Wystąpienie,** **Rozmiar (Bajty),** **Rozmiar włącznie (Bajty)** i **Moduł.**

|||
|-|-|
|**Typ obiektu** lub **wystąpienie**|Nazwa typu lub wystąpienia obiektu.|
|**Liczba odwołań**|Liczba wystąpień typu w migawce podstawowej.|
|**Dyfernek liczby odwołań**|Dla typu różnica w liczbie wystąpień typu między migawki podstawowej i poprzedniej migawki.|
|**Rozmiar (bajty)**|Rozmiar obiektów w podstawowego migawki, mniej rozmiaru obiektów w obiektach. Dla typu **Size (Bajty)** i **Rozmiar włącznie (Bajty)** są sumy rozmiarów wystąpień typu.|
|**Całkowity rozmiar różnicy (bajtów)**|Dla typu różnica w całkowity rozmiar wystąpień typu między migawki podstawowej i poprzedniej migawki, pomniejszonej o rozmiar obiektów w wystąpieniach. |
|**Rozmiar włącznie (bajty)**|Rozmiar obiektów w podstawowego migawki, w tym rozmiar obiektów w obiektach.|
|**Różnice rozmiaru włącznie (bajty)**|Dla typu różnica w rozmiarze wszystkich wystąpień typu między migawki podstawowej i poprzedniej migawki, w tym rozmiar obiektów w obiektach.|
|**Moduł**|Moduł, który zawiera obiekt.|

## <a name="see-also"></a>Zobacz też
- [Pamięć JavaScript](../profiling/javascript-memory.md)
- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
- [Najważniejsze wskazówki dotyczące wydajności aplikacji platformy uniwersalnej systemu Windows w językach C++, C#i Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Diagnozowanie problemów z pamięcią za pomocą nowego narzędzia Użycie pamięci w programie Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)