---
title: Analizowanie użycia pamięci bez debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2018
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
ms.openlocfilehash: 915a46a1f201dab55edb0b0b091c003d6b449049
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873457"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Analizowanie użycia pamięci bez debugera

**Użycie pamięci** narzędzie monitoruje wykorzystanie pamięci aplikacji. To narzędzie umożliwia skutki pamięci w czasie rzeczywistym scenariusze, które aktywnie tworzysz w programie Visual Studio. Szczegółowe migawek stanu pamięci aplikacji i porównywanie migawek, aby dowiedzieć się, że głównych przyczyn problemów z pamięcią.

**Użycie pamięci** narzędzie można uruchomić z lub bez debugera. Poniższe instrukcje przedstawiają sposób użycia **użycie pamięci** narzędzia bez debugera w programie Visual Studio **Profiler wydajności**.

>[!NOTE]
>- Do mierzenia użycia pamięci dla aplikacji platformy .NET Core, należy użyć **użycie pamięci** narzędzie za pomocą debugera. Aby uzyskać instrukcje, zobacz [profilu użycie pamięci w programie Visual Studio](memory-usage.md).
>- Aby Analizowanie użycia pamięci w aplikacjach JavaScript i HTML platformy uniwersalnej systemu Windows, należy użyć [pamięci JavaScript](../profiling/javascript-memory.md) narzędzia w **Profiler wydajności**.

## <a name="memory-usage-diagnostic-sessions"></a>Sesje diagnostyki pamięci użycia

**Aby rozpocząć sesję diagnostyki wykorzystania pamięci:**

1. Otwórz C# projektu Windows (UWP, Universal) w programie Visual Studio.

1. Na pasku menu wybierz **debugowania** > **Profiler wydajności**.

1. Wybierz **użycie pamięci**, a następnie wybierz pozycję **Start**.

   ![Uruchamianie sesji diagnostyki użycie pamięci](../profiling/media/memuse_start_diagnosticssession.png "rozpocząć sesję diagnostyki użycia pamięci")

### <a name="monitor-memory-use"></a>Monitorowanie użycia pamięci

Podczas uruchamiania sesji diagnostycznej uruchamiania aplikacji, a **narzędzia diagnostyczne** okna wyświetlany jest wykres osi czasu użycia pamięci aplikacji.

![Strona przeglądu użycia pamięci](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Wykres osi czasu wahania pamięci jest wyświetlany jako uruchomienia aplikacji. Wartości graniczne na wykresie zazwyczaj wskazują, że jakiś kod jest zbieranie lub tworzenie danych i odrzucanie go po zakończeniu przetwarzania. Duże wartości szczytowe wskazywać obszary, które mogą być w stanie zoptymalizować. Częste więcej jest wzrost użycia pamięci, które nie są zwracane, ponieważ może to oznaczać, nieefektywnego wykorzystania pamięci lub nawet przeciek pamięci.

### <a name="take-snapshots-of-app-memory-states"></a>Wykonywanie migawek stanu pamięci aplikacji

Aplikacja używa dużej liczby obiektów i można skoncentrować się analizy na jeden scenariusz. Lub może się okazać problemy z pamięcią w celu zbadania. Można również tworzyć migawek podczas sesji diagnostycznej do przechwytywania użycie pamięci w szczególności momentach. To dobry pomysł, aby uzyskać dodatkowe migawki i migawką będącą punktem odniesienia w aplikacji przed wyświetleniem problem pamięci, innej migawki po pierwszym wystąpieniu problemu, jeśli można powtarzać tego scenariusza.

Aby zebrać migawki, wybierz **wykonaj migawkę** gdy zachodzi potrzeba przechwycenia danych pamięci.

###  <a name="BKMK_Close_a_monitoring_session"></a> Zamykanie sesji diagnostycznej

Aby zatrzymać sesji monitorowania bez tworzenia raportu, zamknij okno diagnostycznych. Aby wygenerować raport, gdy wszystko będzie gotowe gromadzenie lub migawki, wybierz opcję **Zatrzymaj Kolekcjonowanie**.

![Zatrzymaj zbieranie](../profiling/media/memuse__stopcollection.png "Zatrzymaj zbieranie")

##  <a name="memory-usage-reports"></a>Raporty dotyczące użycia pamięci

Po zatrzymaniu zbierania danych **użycie pamięci** narzędzie zatrzymuje ją i wyświetla **użycie pamięci** strona przeglądu.

![Strona przeglądu użycia pamięci](../profiling/media/memuse__reportoverview1.png "strony Przegląd użycia pamięci")

### <a name="BKMK_Memory_Usage_snapshot_views"></a> Migawki użycia pamięci

Liczby w **migawki** okienka Pokaż bajtów i obiektów w pamięci, gdy każda migawki i różnica między migawki, a poprzednią.

Liczby są łączy, które szczegółowo open **użycie pamięci** raportu widoków w nowych oknach programu Visual Studio. A [raport szczegóły migawki](#snapshot-details-reports) zawiera typy i wystąpienia w jedną migawkę. A [różnica (różnica) raport migawki](#snapshot-difference-diff-reports) porównuje typy i wystąpienia w dwóch migawek.

  ![Wyświetl linki migawki](../profiling/media/memuse__snapshotview_numbered.png "łączy widoku migawki")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Całkowita liczba bajtów w pamięci, gdy migawka została utworzona.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki, posortowane według całkowity rozmiar wystąpienia typu.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Całkowita liczba obiektów w pamięci, gdy migawka została utworzona.<br /><br /> Wybierz ten link, aby wyświetlić raport szczegóły migawki, posortowane według liczby wystąpień typów.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Różnica między łączny rozmiar obiektów w pamięci w tej migawce, a poprzednią migawkę. <br /><br /> Dodatni oznacza, że liczba pamięci rozmiar tej migawki jest większy niż poprzednia, a ujemna oznacza, że liczba rozmiar jest mniejszy. **Plan bazowy** oznacza, że migawka jest pierwszy w sesji diagnostycznej. **Nie różnicy** oznacza, że różnica wynosi zero.<br /><br /> Wybierz ten link, aby wyświetlić raport diff migawki, posortowane według różnica w łącznym rozmiarze wystąpień typów.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Różnica między całkowita liczba obiektów pamięci w tej migawce, a poprzednią migawkę.<br /><br /> Wybierz ten link, aby wyświetlić raport diff migawki, posortowane według różnica w łącznej liczbie wystąpień typów.|

## <a name="memory-usage-snapshot-reports"></a>Raporty migawki użycia pamięci

<a name="BKMK_Snapshot_report_trees"></a> Po wybraniu jednego z linków migawki w **użycie pamięci** raport migawki zostanie otwarta na nowej stronie Strona przeglądu.

![Raport migawki użycia pamięci](../profiling/media/memuse_snapshotreport_all.png "raport migawki użycia pamięci")

W raporcie migawki można rozwinąć **typu obiektu** wpisów, aby wyświetlić wpisy podrzędnych. Nazwy są unikatowe identyfikatory, które są generowane przez narzędzie użycie pamięci.

Jeśli **typu obiektu** jest niebieski, możesz wybrać go, aby przejść do obiektu w kodzie źródłowym w osobnym oknie.

Typy, nie można zidentyfikować lub którego zaangażowania w kodzie, którego nie rozumiesz są prawdopodobnie .NET Framework, system operacyjny lub kompilatora obiektów. **Użycie pamięci** narzędzie wyświetli te obiekty, jeśli są one związane z łańcucha własności obiektów.

W raporcie migawki:

- **Sterty zarządzanej** drzewa zawiera typy i wystąpienia w raporcie. Wybierając typ lub wystąpienie Wyświetla **ścieżki do obiektu głównego** i **przywoływane obiekty** drzewa dla wybranego elementu.

- **Ścieżki do obiektu głównego** drzewa pokazuje łańcuch obiektów, które odwołują się typ lub wystąpienie. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.

- **Przywoływane typy** lub **przywoływane obiekty** drzewa zawiera obiekty, które odwołuje się do wybranego typu lub wystąpienia.

###  <a name="BKMK_Report_tree_filters_"></a> Filtry drzewa raportu

Wiele typów w aplikacji nie są bardzo interesujące dla deweloperów aplikacji. Filtry raportów migawki można ukryć większość z tych typów w **sterty zarządzanej** i **ścieżki do obiektu głównego** drzewa.

![Opcje sortowania i filtrowania](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a> Aby filtrować drzewa według nazwy typu, wprowadź nazwę w **filtru** pole. Filtr nie jest rozróżniana wielkość liter i rozpoznaje określonego ciągu w dowolnej części nazwy typu.

- <a name="BKMK_Collapse_Small_Objects"></a> Wybierz **Zwiń małe obiekty** w **filtru** listę rozwijaną, aby ukryć typy, których **rozmiar (w bajtach)** jest mniejsza niż 0,5 procent całkowitej ilości pamięci.

- <a name="BKMK_Just_My_Code"></a> Wybierz **tylko mój kod** w **filtru** listę rozwijaną, aby ukryć największą liczbą wystąpień, które zostały wygenerowane przez kod zewnętrzny. Typy zewnętrzne należą do systemu operacyjnego lub składnikami ramach lub są generowane przez kompilator.

## <a name="snapshot-details-reports"></a>Migawka szczegóły raportów

 Raport szczegóły migawki opisuje jedną migawkę z sesji diagnostycznej. Aby otworzyć raport, wybierz link rozmiaru lub obiektów w okienku migawki.

 ![Łącza do raportu migawek w okienku migawki](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "łącza do raportu migawek w okienku migawki")

Oba łącza otwarcie tego samego raportu. Jedyna różnica polega na kolejności sortowania począwszy od **sterty zarządzanej** drzewa. Link rozmiar sortuje raport według **całkowity rozmiar (w bajtach)** kolumny. Łącza obiektów sortuje raport według **liczba** kolumny. Po otwarciu raportu można zmienić kolumny sortowania lub zamówienia.

###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Zarządzane drzewa sterty (Raporty migawki szczegóły)
 **Sterty zarządzanej** drzewa zawiera listę typów obiektów, które są przechowywane w pamięci. Rozwiń nazwę typu, aby wyświetlić 10 największych wystąpienia typu, posortowane według rozmiaru. Wybierz typ lub wystąpienie, aby wyświetlić **ścieżki do obiektu głównego** i **przywoływane obiekty** drzewa dla wybranego elementu.

 ![Zarządzany stos drzewa](../profiling/media/memuse__snapshotdetails_managedheaptree.png "drzewa sterty zarządzanej")

**Sterty zarządzanej** drzewa w raporcie szczegóły migawki zawiera następujące kolumny:

|||
|-|-|
|**Typ obiektu**|Nazwa wystąpienia typu lub obiektu.|
|**Liczba**|Liczba wystąpień obiektu tego typu. **Liczba** ma zawsze numer 1 dla wystąpienia.|
|**Rozmiar (bajty)**|Dla typu, rozmiaru wszystkich wystąpień typu w migawce mniejszy rozmiar obiektów zawartych w wystąpienia.<br /><br /> W przypadku wystąpienia rozmiar mniej rozmiar obiektów zawartych w wystąpieniu obiektu. |
|**Całkowity rozmiar (w bajtach)**|Rozmiar wystąpienia typu lub rozmiaru pojedyncze wystąpienie, takich jak rozmiar zawartych obiektów.|
|**Module**|Moduł, który zawiera obiekt.|

###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Ścieżki do katalogu głównego drzewa (migawka szczegóły raportów)
**Ścieżki do katalogu głównego drzewa** pokazuje łańcuch obiektów, które odwołują się typ lub wystąpienie. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.

Dla typu w **ścieżki do obiektu głównego** liczbę obiektów, które zawierają odwołania do tego typu jest wyświetlana w drzewie **licznik odwołań** kolumny.

![Ścieżki do katalogu głównego drzewa dla typów](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "ścieżki do katalogu głównego drzewa dla typów")

###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Przywoływane typy lub do których odwołuje się obiekty drzewa (migawka szczegóły raportów)
**Przywoływane typy** lub **przywoływane obiekty** drzewa zawiera obiekty, które odwołuje się do wybranego typu lub wystąpienia.

![Przywoływane obiekty drzewa dla wystąpień](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "drzewa obiektów, do których odwołuje się do wystąpienia")

A **przywoływane typy** drzewa w raporcie szczegóły migawki zawiera następujące kolumny. A **przywoływane obiekty** drzewa nie ma **licznik odwołań** kolumny.

|||
|-|-|
|**Typ obiektu** lub **wystąpienia**|Nazwa typu lub wystąpienia.|
|**Liczba odwołań**|W przypadku typów wystąpień obiektu tego typu.|
|**Rozmiar (bajty)**|Dla typu, rozmiaru wszystkich wystąpień tego typu, mniej rozmiar obiektów znajdujących się w typie.<br /><br /> W przypadku wystąpienia rozmiar obiektu mniej rozmiar obiektów zawartych w obiekcie.|
|**Całkowity rozmiar (w bajtach)**|Całkowity rozmiar wystąpienia typu lub rozmiar wystąpienia, takich jak rozmiar zawartych obiektów.|
|**Module**|Moduł, który zawiera obiekt.|

## <a name="snapshot-difference-diff-reports"></a>Raporty migawki różnica (różnica)

Raport migawki różnica (różnica) pokazuje zmiany między podstawowym migawki i poprzedniej migawki. Aby otworzyć raport różnic, wybierz jeden z łącza różnica w okienku migawki.

Oba łącza otwarcie tego samego raportu. Jedyna różnica polega na kolejności sortowania począwszy od **sterty zarządzanej** drzewa w raporcie. Link rozmiar sortuje raport według **różnica w rozmiarze włącznie (w bajtach)** kolumny. Łącza obiektów sortuje raport według **różnicy liczby** kolumny. Po otwarciu raportu można zmienić kolumny sortowania lub zamówienia.

 ![Łącza do różnicy raportu w okienku migawki](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "łącza do różnicy raportu w okienku migawki")

###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Zarządzane drzewa sterty (Raporty migawki różnic)

 **Sterty zarządzanej** drzewa zawiera listę typów obiektów, które są przechowywane w pamięci. Można rozwinąć nazwę typu, aby wyświetlić 10 największych wystąpienia typu, posortowane według rozmiaru. Wybierz typ lub wystąpienie, aby wyświetlić **ścieżki do obiektu głównego** i **przywoływane obiekty** drzewa dla wybranego elementu.

 ![Drzewo stosu zarządzanego dla typu w raporcie różnica](../profiling/media/memuse_snapshotdiff_type_heap.png "sterty zarządzanej drzewa dla typu w raporcie różnicy")

**Sterty zarządzanej** drzewa w raporcie diff migawki zawiera następujące kolumny:

|||
|-|-|
|**Typ obiektu**|Nazwa wystąpienia typu lub obiektu.|
|**Liczba**|Liczba wystąpień typu podstawowego migawki. **Liczba** ma zawsze numer 1 dla wystąpienia.|
|**Różnica liczby**|Dla typu, różnią się w liczbie wystąpień typu podstawowego migawki i poprzednią migawkę. To pole jest puste w przypadku wystąpienia.|
|**Rozmiar (bajty)**|Rozmiar obiektów w migawce podstawowego, mniej rozmiar obiektów w obiektach. Dla typu **rozmiar (w bajtach)** i **całkowity rozmiar (w bajtach)** są sumy rozmiarów wystąpień typu.|
|**Diff całkowity rozmiar (w bajtach)**|Dla typu, różnią się w całkowity rozmiar wystąpienia typu podstawowego migawki i poprzednią migawkę, mniej rozmiar obiektów w wystąpieniach. To pole jest puste w przypadku wystąpienia.|
|**Całkowity rozmiar (w bajtach)**|Rozmiar obiektów w migawce podstawowego, takich jak rozmiar obiektów w obiektach.|
|**Różnica w rozmiarze włącznie (w bajtach)**|Dla typu, różnią się rozmiar wszystkich wystąpień tego typu podstawowego migawki i poprzednią migawkę, takich jak rozmiar obiektów w obiektach. To pole jest puste w przypadku wystąpienia.|
|**Module**|Moduł, który zawiera obiekt.|

###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Ścieżki do katalogu głównego drzewa (Raporty migawki różnic)

**Ścieżki do katalogu głównego drzewa** pokazuje łańcuch obiektów, które odwołują się typ lub wystąpienie. Moduł zbierający elementy bezużyteczne .NET Framework Czyści pamięć dla obiektu, tylko wtedy, gdy wszystkie odwołania do niego zostały zwolnione.

Dla typu w **ścieżki do obiektu głównego** liczbę obiektów, które zawierają odwołania do tego typu jest wyświetlana w drzewie **licznik odwołań** kolumny. Różnica w liczbie od poprzedniej migawki jest **Diff odwołanie** kolumny.

 ![Ścieżki do katalogu głównego drzewa w raporcie diff](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "ścieżki do katalogu głównego drzewa w raporcie różnic")

###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Przywoływane typy lub odwołanie do obiektów w drzewie (Raporty migawki różnic)

**Przywoływane typy** lub **przywoływane obiekty** drzewa zawiera obiekty, które odwołuje się do wybranego typu lub wystąpienia.

![Przywoływane typy w raporcie diff](../profiling/media/memuse_snapshotdiff_referencedtypes.png "przywoływane typy w raporcie różnic")

A **przywoływane typy** drzewa w raporcie diff migawki zawiera następujące kolumny. A **przywoływane obiekty** drzewo **wystąpienia**, **rozmiar (w bajtach)**, **całkowity rozmiar (w bajtach)**, i **modułu** kolumn.

|||
|-|-|
|**Typ obiektu** lub **wystąpienia**|Nazwa wystąpienia typu lub obiektu.|
|**Liczba odwołań**|Liczba wystąpień typu podstawowego migawki.|
|**Różnica w liczbie odwołań**|Dla typu, różnią się w liczbie wystąpień typu podstawowego migawki i poprzednią migawkę.|
|**Rozmiar (bajty)**|Rozmiar obiektów w migawce podstawowego, mniej rozmiar obiektów w obiektach. Dla typu **rozmiar (w bajtach)** i **całkowity rozmiar (w bajtach)** są sumy rozmiarów wystąpień typu.|
|**Diff całkowity rozmiar (w bajtach)**|Dla typu, różnią się w całkowity rozmiar wystąpienia typu podstawowego migawki i poprzednią migawkę, mniej rozmiar obiektów w wystąpieniach. |
|**Całkowity rozmiar (w bajtach)**|Rozmiar obiektów w migawce podstawowego, takich jak rozmiar obiektów w obiektach.|
|**Różnica w rozmiarze włącznie (w bajtach)**|Dla typu, różnią się rozmiar wszystkich wystąpień tego typu podstawowego migawki i poprzednią migawkę, takich jak rozmiar obiektów w obiektach.|
|**Module**|Moduł, który zawiera obiekt.|

## <a name="see-also"></a>Zobacz także
- [Pamięć języka JavaScript](../profiling/javascript-memory.md)
- [Profilowanie w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
- [Wydajność — najlepsze rozwiązania dla aplikacji platformy uniwersalnej systemu Windows przy użyciu języka C++, C# i Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Diagnozowanie problemów z pamięcią za pomocą nowe narzędzie użycie pamięci w programie Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706)