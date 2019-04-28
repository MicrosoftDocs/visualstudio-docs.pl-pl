---
title: Analizowanie problemów pamięci .NET Framework | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e78cefa9778e2889130f865e4c61cc8a97014db7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444659"
---
# <a name="analyze-net-framework-memory-issues"></a>Analiza problemów pamięci .NET Framework
Wyszukiwanie przecieków pamięci i pamięci nieefektywne, użyj w kodzie .NET Framework za pomocą programu Visual Studio zarządzany analizator pamięci. Minimalna wersja systemu .NET Framework kod docelowy jest .NET Framework 4.5.  
  
 Narzędzia analizy pamięci analizuje informacje zawarte w *pliki zrzutu ze danych sterty* , kopia obiektów w pamięci aplikacji. Możesz zbierać pliki zrzutu (.dmp) z programu Visual Studio IDE lub przy użyciu innych narzędzi systemu.  
  
- Możesz analizować pojedynczej migawki zrozumieć konsekwencje typów obiektów na wykorzystanie pamięci i znaleźć kod w swojej aplikacji, która używa pamięci nieefektywne.  
  
- Można również porównać (*diff*) Użyj dwóch migawki znajdowanie obszarów w kodzie aplikacji, które powodują pamięci, aby zwiększyć wraz z upływem czasu.  
  
  Aby zapoznać się z przewodnikiem zarządzany analizator pamięci, zobacz [przy użyciu programu Visual Studio 2013 do diagnozowania problemów pamięci .NET w środowisku produkcyjnym](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) w Visual Studio ALM + Team Foundation Server blog.  
  
## <a name="BKMK_Contents"></a> Zawartość  
 [Wykorzystanie pamięci w aplikacjach .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Zidentyfikuj problem pamięci w aplikacji](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Zbieraj migawki pamięci](#BKMK_Collect_memory_snapshots)  
  
 [Analiza użycia pamięci](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Wykorzystanie pamięci w aplikacjach .NET Framework  
 .NET Framework jest jesdnostką zbierającą śmieci środowiska uruchomieniowego, aby w przypadku większości aplikacji, wykorzystanie pamięci nie jest problemem. Jednak w długo działających aplikacji, takich jak usługi sieci web i aplikacje, a na urządzeniach, które mają ograniczoną ilość pamięci, gromadzenie obiektów w pamięci może mieć wpływ na wydajność aplikacji i urządzeń, która działa na. Użycie zbyt dużej ilości pamięci może zablokować aplikację i maszynę zasobów, jeśli moduł odśmiecania pamięci jest uruchamiany zbyt często, czy system operacyjny jest zmuszony do przenoszeniu ich do pamięci RAM i dysku. W najgorszym przypadku aplikacja może ulec awarii z powodu wyjątku "za mało pamięci".  
  
 .NET *sterty zarządzanej* to region pamięci wirtualnej, gdzie są przechowywane odwołania obiekty utworzone przez aplikację. Okres istnienia obiektów są zarządzane przez wyrzucanie elementów bezużytecznych (GC). Moduł zbierający elementy bezużyteczne używa odwołania do śledzenia obiektów, które zajmują bloki pamięci. Odwołanie jest tworzony, gdy obiekt zostanie utworzone i przypisane do zmiennej. Pojedynczy obiekt może mieć wiele odwołań. Na przykład dodatkowe informacje do obiektu może można utworzyć, dodając obiekt do klasy, kolekcji lub innymi struktura danych lub przez przypisanie obiektu do drugiego zmiennej. Mniej oczywistych sposobem tworzenia odwołanie jest jeden obiekt, dodając procedurę obsługi zdarzeń innego obiektu. W tym przypadku drugi obiekt przechowuje odwołanie do pierwszego obiektu, dopóki program obsługi jest jawnie usuwany lub drugi obiekt zostanie zniszczony.  
  
 Dla każdej aplikacji GC zachowuje drzewa odwołania, służącą do śledzenia obiektów, odwołuje się aplikacja. *Drzewa odwołanie* ma zbiór obiektów głównych, w tym obiektów globalnych i statycznych, a także stosy skojarzony wątek i dynamicznie utworzyć wystąpienia obiektów. Obiekt jest ścieżką, jeśli obiekt ma co najmniej jeden obiekt nadrzędny, który zawiera odwołanie do niego. Wykaz Globalny mógł odzyskać pamięć obiektu, tylko wtedy, gdy żaden obiekt lub zmienna w aplikacji ma odwołanie do niej.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Zidentyfikuj problem pamięci w aplikacji  
 Najbardziej widoczne objawem problemów z pamięcią jest wydajności aplikacji, szczególnie w przypadku spadku wydajności wraz z upływem czasu. Obniżenie wydajności innych aplikacji, podczas gdy Twoja aplikacja działa również może wskazywać problem z pamięci. Jeśli podejrzewasz problem pamięci, skorzystaj z narzędzia, takie jak Menedżer zadań lub [Windows Performance Monitor](http://technet.microsoft.com/library/cc749249.aspx) zmuszony do dalszego badania. Na przykład wyszukaj wzrost całkowity rozmiar pamięci, która nie może wyjaśniać potencjalnym źródłem przecieki pamięci:  
  
 ![Zgodne pamięci wzrost Monitor zasobów](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Może także zauważyć, że wartości graniczne pamięci, które są większe niż moglibyśmy swojej wiedzy na temat kod, który może wskazywać nieefektywnego wykorzystania pamięci w procedurze:  
  
 ![Wartości graniczne pamięci w usłudze Resource Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Zbieraj migawki pamięci  
 Narzędzia analizy pamięci analizuje informacje zawarte w *pliki zrzutu* zawierających informacje o stercie. Można tworzyć pliki zrzutu w programie Visual Studio lub można użyć narzędzia, takiego jak [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) z [Windows Sysinternals](http://technet.microsoft.com/sysinternals). Zobacz [co to jest zrzut, i jak mogę utworzyć jeden?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) na blogu zespołu debugera Visual Studio.  
  
> [!NOTE]
> Większość narzędzi może zbierać informacji zrzutu z lub bez niego dane pamięci sterty ukończone. Analizator pamięci programu Visual Studio wymaga informacji pełnego stosu.  
  
 **Aby zebrać zrzut z programu Visual Studio**  
  
1. Można utworzyć pliku zrzutu dla procesu, który został uruchomiony z projektu programu Visual Studio, lub można dołączyć debuger do działającego procesu. Zobacz [dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Zatrzymaj wykonywanie. Debuger zatrzymuje się po wybraniu **Przerwij wszystko** na **debugowania** menu lub w sytuacji wyjątku lub w punkcie przerwania  
  
3. Na **debugowania** menu, wybierz **Zapisz zrzut jako**. W **Zapisz zrzut jako** okna dialogowego pole, określ lokalizację i upewnij się, że **minizrzutu ze stertą** (ustawienie domyślne) jest zaznaczona w **Zapisz jako typ** listy.  
  
   **Porównanie dwóch migawek pamięci**  
  
   Aby analizować wzrost użycia pamięci aplikacji, należy zebrać dwa pliki zrzutu z pojedynczego wystąpienia aplikacji.  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analiza użycia pamięci  
 [Filtruj listę obiektów](#BKMK_Filter_the_list_of_objects) **&#124;** [analizy danych pamięci z jednego migawki](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [porównanie dwóch pamięci migawki](#BKMK_Compare_two_memory_snapshots)  
  
 Do analizowania pliku zrzutu pamięci Użyj problemy:  
  
1. W programie Visual Studio, wybierz **pliku**, **Otwórz** i określ plik zrzutu.  
  
2. Na **Podsumowanie pliku minizrzutu** wybierz **Debuguj pamięć zarządzaną**.  
  
    ![Strona podsumowania pliku zrzutu](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Analizator pamięci uruchamia sesję debugowania do analizowania pliku i wyświetla wyniki na stronie widok sterty:  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filtruj listę obiektów  
 Domyślnie analizator pamięci filtruje listę obiektów w migawce pamięci, aby wyświetlić tylko typy i wystąpienia, które są kod użytkownika, a także aby pokazać tylko te typy, których łączny rozmiar włącznie przekracza wartość progową odsetek całkowity rozmiar sterty. Można zmienić tych opcji w **ustawienia widoku** listy:  
  
|||  
|-|-|  
|**Włącz opcję tylko mój kod**|Tylko mój kod ukrywa najbardziej typowe obiekty systemowe, tak aby tylko typy, które tworzysz są wyświetlane na liście.<br /><br /> Możesz również ustawić opcję tylko mój kod w programie Visual Studio **opcje** okno dialogowe. Na **debugowania** menu, wybierz **opcje i ustawienia**. W **debugowanie**/**ogólne** karty, wybierz lub wyczyść **tylko mój kod**.|  
|**Zwiń małe obiekty**|**Zwiń małe obiekty** ukrywa wszystkie typy, których łączny rozmiar (włącznie) jest mniejsza niż 0,5 procent całkowity rozmiar sterty.|  
  
 Lista typów można również filtrować, wprowadzając ciąg w **wyszukiwania** pole. Na liście zostaną wyświetlone tylko te typy, których nazwy zawierają ciąg.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analizowanie danych pamięci z jednego migawki  
 Visual Studio uruchamia nową sesję debugowania, analizowanie pliku i wyświetla dane w pamięci w oknie Widok sterty.  
  
 ![The Object Type list](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Tabela typów obiektów  
 W górnym tabeli wymieniono typy obiektów, które są przechowywane w pamięci.  
  
- **Liczba** pokazuje liczbę wystąpień typu w migawce.  
  
- **Rozmiar (w bajtach)** to rozmiar wszystkich wystąpień tego typu, z wyłączeniem rozmiar przechowuje odwołania do obiektów. Program  
  
- **Całkowity rozmiar (w bajtach)** zawiera rozmiary obiektów, do którego istnieje odwołanie.  
  
  Możesz wybrać ikonę wystąpienia (![ikonę wystąpienia, w kolumnie Typ obiektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) w **typu obiektu** kolumny, aby wyświetlić listę wystąpień Typ.  
  
#### <a name="instance-table"></a>Tabela wystąpienia  
 ![Instances table](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Wystąpienie** jest lokalizację obiektu, który służy jako identyfikator obiektu obiektu w pamięci  
  
- **Wartość** pokazuje rzeczywistej wartości typów wartości. Możesz umieścić kursor nazwę typu odwołania, aby wyświetlić jej wartości danych w oknie z poradami danych.  
  
   ![Wystąpienie wartości w oknie z poradami danych](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Rozmiar (w bajtach)** to rozmiar obiektu, z wyłączeniem rozmiar przechowuje odwołania do obiektów. Program  
  
- **Całkowity rozmiar (w bajtach)** zawiera rozmiary obiektów, do którego istnieje odwołanie.  
  
  Domyślnie, typy i wystąpienia są sortowane według **całkowity rozmiar (w bajtach)**. Wybierz nagłówek kolumny na liście, aby zmienić kolejność sortowania.  
  
#### <a name="paths-to-root"></a>Ścieżki do obiektu głównego  
  
- Dla typu wybrana w zaufanym **typu obiektu** tabeli **ścieżki do obiektu głównego** tabeli przedstawiono hierarchie typu unikatowego, które zachęcają do obiektów głównych dla wszystkich obiektów wraz z liczbą odwołania do typu Typ, który znajduje się nad nim w hierarchii.  
  
- Dla obiektu wybranego w wystąpieniu typu **ścieżki do obiektu głównego** przedstawia wykres rzeczywistych obiektów, które zawierają odwołania do wystąpienia. Możesz umieścić kursor nazwę obiektu, aby wyświetlić jej wartości danych w oknie z poradami danych.  
  
#### <a name="referenced-types--referenced-objects"></a>Przywoływane typy / przywoływane obiekty  
  
- Dla typu wybrana w zaufanym **typu obiektu** tabeli **przywoływane typy** karta przedstawia rozmiaru i liczby dla wskazanych typów posiadanych przez wszystkich obiektów wybranego typu.  
  
- Dla wybranego wystąpienia typu **przywoływane obiekty** zawiera obiekty, które są przechowywane w wybranym wystąpieniu. Możesz umieścić kursor nazwę aby wyświetlić jej wartości danych w oknie z poradami danych.  
  
  **Odwołania cykliczne**  
  
  Drugi obiekt, który bezpośrednio lub pośrednio zawiera odwołanie do pierwszego obiektu można odwoływać się do obiektu. Analizator pamięci napotka tę sytuację, zatrzyma rozszerzanie ścieżki odwołania i dodaje **[wykryto cykl]** adnotację do tej listy pierwszego obiektu i zatrzymuje.  
  
  **Typy głównego**  
  
  Analizator pamięci dodaje adnotacje do obiektów głównych, które opisuje typ odwołania, który jest zablokowany:  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|**Zmienna statyczna** `VariableName`|Zmienna statyczna. `VariableName` to nazwa zmiennej.|  
|**Dojście finalizacji**|Odwołanie z; kolejka finalizatorów|  
|**Zmienna lokalna**|Zmienna lokalna.|  
|**Silne dojście**|Dojście do silne odwołanie z tabeli uchwyt obiektu.|  
|**Asynchroniczne. Przypięte dojście**|Asynchroniczny obiekt przypięte z tabelę uchwytów obiektu.|  
|**Dojście zależne**|Obiekt zależny od tabeli uchwyt obiektu.|  
|**Przypięte dojście**|Przypięte silne odwołanie z tabeli uchwyt obiektu.|  
|**Dojście RefCount**|Obiekt zliczonych odwołań z tabeli uchwyt obiektu.|  
|**Dojście SizedRef**|Silne dojście, który utrzymuje Przybliżony rozmiar zbiorowe zamknięcia wszystkich obiektów i korzenie obiektów w czasie kolekcji wyrzucania elementów.|  
|**Przypięta zmienna lokalna**|Przypiętej zmiennej lokalnej.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Porównanie dwóch migawek pamięci  
 Możesz porównać dwa pliki zrzutu procesu do znajdowania obiektów, które mogą być przyczyną przecieków pamięci. Interwał między zbiór pierwszy (wcześniej) i drugi plik (później) powinien być wystarczająco duży, że wzrost liczby obiektów ujawnione jest jasne, łatwo. Aby porównać dwa pliki:  
  
1. Otwieranie pliku zrzutu drugiej, a następnie wybierz **Debuguj pamięć zarządzaną** na **Podsumowanie pliku minizrzutu** strony.  
  
2. Na stronie raportu analizy pamięci, należy otworzyć **wybierz linii bazowej** , a następnie wybierz **Przeglądaj** Aby określić pierwszy plik zrzutu.  
  
   Analizator dodaje kolumn do górnego okienka raportu, wyświetlające różnica między **liczba**, **rozmiar**, i **rozmiarze włącznie** typów do tych wartości w wcześniej migawkę.  
  
   ![Diff kolumn na liście typów](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **różnicy licznika odwołań** kolumny jest także dodawane do **ścieżki do obiektu głównego** tabeli.  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Blog dotyczący programu VS ALM w programie TFS: Za pomocą programu Visual Studio 2013 do diagnozowania problemów z pamięcią .NET w środowisku produkcyjnym](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV &#124; Managed Memory Analysis](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio Toolbox &#124; Managed Memory Analysis in Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)