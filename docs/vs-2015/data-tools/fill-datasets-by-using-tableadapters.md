---
title: Wypełnij zestawów danych za pomocą adapterów TableAdapter | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4c036cac8fa60e3f0353815cb3790f0f74ddc77
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656781"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Wypełnij zestawów danych za pomocą adapterów TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Składnik TableAdapter wypełnia zestawu danych danymi z bazy danych na podstawie jednego lub więcej zapytań lub procedur składowanych, które określisz. TableAdapters można również wykonać dodaje, aktualizuje i usuwa w bazie danych, aby zachować zmiany wprowadzone do zestawu danych. Można także wystawić polecenia globalne, które nie są związane z żadną z tabel.  
  
> [!NOTE]
>  TableAdapters są generowane przez projektantów programu Visual Studio. Jeśli programowe tworzenie zestawów danych użyj DataAdapter jest klasą .NET Framework.  
  
 Aby uzyskać szczegółowe informacje o operacjach TableAdapter możesz pominąć bezpośrednio do jednego z tych tematów:  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Jak użyć projektantów do tworzenia i konfigurowanie adapterów TableAdapter|  
|[Tworzenie sparametryzowanych zapytań adaptera TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Jak umożliwić użytkownikom umożliwiają określanie wartości argumentów do procedury TableAdapter lub zapytania|  
|[Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Sposób użycia metod dbdirect — TableAdapters|  
|[Wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Jak pracować z ograniczenia foreign key, podczas aktualizowania danych|  
|[Jak rozszerzanie funkcjonalności adaptera TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Jak dodawać niestandardowego kodu do TableAdapters|  
|[Odczytywanie danych XML do zestawu danych](../data-tools/read-xml-data-into-a-dataset.md)|Jak pracować z danymi XML|  
  
## <a name="tableadapters-overview"></a>Omówienie adapterów TableAdapter  
 TableAdapters są wygenerowany przez projektanta składników, które nawiązać połączenie z bazą danych, wykonywania zapytań lub procedur przechowywanych i wypełnienie ich DataTable zwracanych danych. TableAdapters również wysyłać zaktualizowane dane z aplikacji w bazie danych. Można uruchomić dowolną liczbę zapytań dowolną w metodzie TableAdapter tak długo, jak zwracają danych, który jest zgodny schemat tabeli, z którym jest skojarzona TableAdapter. Na poniższym diagramie przedstawiono, jak TableAdapters wchodzić w interakcje z bazami danych i innych obiektów w pamięci:  
  
 ![Przepływ danych w aplikacji klienckiej](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Gdy TableAdapters są skonstruowane z **Projektanta obiektów Dataset**, klasy TableAdapter nie są generowane jako klas zagnieżdżonych <xref:System.Data.DataSet>. Znajdują się one w oddzielnych przestrzeniach nazw, które są specyficzne dla każdego zestawu danych. Na przykład, jeśli masz zestaw danych o nazwie `NorthwindDataSet`, TableAdapter, które są skojarzone z <xref:System.Data.DataTable>s w `NorthwindDataSet` będą miały `NorthwindDataSetTableAdapters` przestrzeni nazw. Aby uzyskać dostęp do określonego TableAdapter programowo, należy zadeklarować nowe wystąpienie klasy TableAdapter. Na przykład:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Associated DataTable schema  
 Gdy utworzysz TableAdapter, użyj początkowego zapytania lub skojarzonej procedurę przechowywaną, aby zdefiniować schemat TableAdapter <xref:System.Data.DataTable>. Uruchomienie tego początkowego zapytania lub procedurę składowaną przez wywołanie metody TableAdapter `Fill` — metoda (która wypełnia TableAdapter skojarzonej <xref:System.Data.DataTable>). Wszelkie zmiany wprowadzone do zapytanietableadapter główne są odzwierciedlane w schemat tabeli powiązane dane. Na przykład usunięcie kolumny z główne zapytanie spowoduje również usunięcie kolumny z tabeli powiązane dane. Jeśli żadnych dodatkowych kwerend w metodzie TableAdapter używa instrukcji SQL, które zwracają kolumn, które nie znajdują się w głównym zapytania, Projektant próbuje synchronizować zmiany kolumn między kwerendy głównych i dodatkowych kwerend. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Polecenia aktualizacji TableAdapter  
 Funkcja aktualizacji TableAdapter jest zależna od ilości informacji jest dostępnych w główne zapytanie w Kreatorze TableAdapter. Na przykład adapterów TableAdapter, które są skonfigurowane do pobierania wartości z wielu tabel (sprzężenia), wartości skalarnych, widokach lub wyniki funkcji agregujących nie są wstępnie utworzone za pomocą możliwość wysyłania aktualizacji do podstawowej bazy danych. Jednak należy skonfigurować ręcznie w poleceń INSERT, UPDATE i DELETE **właściwości** okna.  
  
## <a name="tableadapter-queries"></a>TableAdapter— Zapytania  
 ![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapters może zawierać wiele zapytań do wypełnienia ich tabele powiązane dane. Można zdefiniować dowolną liczbę zapytań dotyczących TableAdapter wymaga aplikacji, tak długo, jak każda kwerenda zwraca dane, który jest zgodny do tego samego schematu jako jej skojarzone dane tabeli. Ta możliwość włączenia TableAdapter załadować różne wyniki na podstawie różnych kryteriów.  
  
 Na przykład jeśli aplikacja zawiera tabelę z nazw klienta, można utworzyć zapytanie, które wypełnia tabelę z każdej nazwy klienta, który zaczyna się od określonej litery, a druga które wypełnia tabelę wszystkich klientów, które znajdują się w tym samym stanie. Aby wypełnić `Customers` tabeli z klientami w danym stanie, możesz utworzyć `FillByState` zapytanie, które przyjmuje parametr na wartość stanu w następujący sposób: `SELECT * FROM Customers WHERE State = @State`. Uruchom zapytanie, wywołując `FillByState` metody i przekazywanie w wartości parametru podobnie do następującego: `CustomerTableAdapter.FillByState("WA")`.  
  
 Oprócz dodawania zapytania, które zwracają dane tego samego schematu jako tabela danych TableAdapter, można dodać zapytania, które zwracają wartości skalarnych (pojedynczą). Na przykład, zapytanie zwracające liczbę klientów (`SELECT Count(*) From Customers`) jest nieprawidłowa dla `CustomersTableAdapter,` mimo że zwrócone dane nie są zgodne ze schematem tabeli.  
  
## <a name="clearbeforefill-property"></a>Właściwość ClearBeforeFill  
 Domyślnie za każdym razem, gdy uruchamiasz zapytanie w celu wypełnienia tabeli danych TableAdapter, istniejące dane są usuwane, a tylko wyniki zapytania są ładowane do tabeli. Ustaw TableAdapter `ClearBeforeFill` właściwość `false` Jeśli chcesz dodać lub scalania danych, która jest zwracana w wyniku zapytania do istniejących danych w tabeli danych. Niezależnie od tego, czy możesz wyczyścić dane Musisz jawnie wysyłania aktualizacji w bazie danych, jeśli chcesz zachować je. Dlatego pamiętaj, aby zapisać wszystkie zmiany danych w tabeli przed uruchomieniem innego zapytania, które wypełnia tabelę. Aby uzyskać więcej informacji, zobacz [aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Dziedziczenie TableAdapter  
 TableAdapters rozszerzają funkcjonalność kart danych w warstwie standardowa poprzez hermetyzację skonfigurowanego <xref:System.Data.Common.DataAdapter> klasy? qualifyHint = False & autoUpgrade = True. Domyślnie, dziedziczy TableAdapter <xref:System.ComponentModel.Component> klasy i nie można rzutować <xref:System.Data.Common.DataAdapter> klasy. Rzutowanie TableAdapter do <xref:System.Data.Common.DataAdapter> klasy skutkuje <xref:System.InvalidCastException> błąd? qualifyHint = False & autoUpgrade = True. Aby zmienić klasę bazową klasy TableAdapter, możesz wpisać klasę, która pochodzi od klasy <xref:System.ComponentModel.Component> w **klasy bazowej** właściwość obiektu TableAdapter w **Projektanta obiektów Dataset**.  
  
## <a name="tableadapter-methods-and-properties"></a>Właściwości i metody TableAdapter  
 Klasa TableAdapter nie jest częścią [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Oznacza to, że nie można wyszukać ją w dokumentacji lub **przeglądarki obiektów**. Jest on tworzony w czasie projektowania, używając jednego z kreatorów, o których wspomniano wcześniej. Nazwa, która jest przypisana do TableAdapter podczas jego tworzenia opiera się na nazwę tabeli, którą pracujesz. Na przykład po utworzeniu na podstawie tabeli w bazie danych o nazwie TableAdapter `Orders`, nosi nazwę TableAdapter `OrdersTableAdapter`. Nazwa klasy TableAdapter można zmienić za pomocą **nazwa** właściwość **Projektanta obiektów Dataset**.  
  
 Poniżej przedstawiono najczęściej używanych metod i właściwości działania TableAdapters:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`TableAdapter.Fill`|Wypełnia TableAdapter skojarzone dane tabeli z wynikami polecenia SELECT TableAdapter.|  
|`TableAdapter.Update`|Wysyła zmiany w bazie danych i zwraca liczbę całkowitą reprezentującą liczbę wierszy, aktualizacja dotyczy. Aby uzyskać więcej informacji, zobacz [aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Zwraca nowy <xref:System.Data.DataTable> , jest wypełniany danymi.|  
|`TableAdapter.Insert`|Tworzy nowy wiersz w tabeli danych. Aby uzyskać więcej informacji, zobacz [wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|Określa, czy tabela danych jest opróżniany przed wywołaniem jednego z `Fill` metody.|  
  
## <a name="tableadapter-update-method"></a>Metoda aktualizacji TableAdapter  
 TableAdapters polecenia danych do odczytu i zapisu z bazy danych. TableAdapter w początkowej `Fill` zapytania (główną) jest używany jako podstawa do tworzenia schemat tabeli powiązane dane, jak również `InsertCommand`, `UpdateCommand`, i `DeleteCommand` poleceń, które są skojarzone z `TableAdapter.Update` metody. Wywoływanie TableAdapter `Update` metoda uruchomienia instrukcji, które zostały utworzone podczas TableAdapter pierwotnie był skonfigurowany, nie dodatkowych zapytań, które zostało dodane z **Kreatora konfiguracji zapytania TableAdapter**.  
  
 Używając TableAdapter skutecznie wykonuje te same operacje za pomocą poleceń, które zazwyczaj będzie wykonywać. Na przykład gdy wywołujesz karty `Fill` metody, karta uruchamia polecenie danych jego `SelectCommand` właściwości i używa czytnik danych (na przykład <xref:System.Data.SqlClient.SqlDataReader>) można załadować zestawu wyników do tabeli danych. Podobnie, gdy zostanie wywołana karty `Update` metody uruchamia odpowiednie polecenie (w `UpdateCommand`, `InsertCommand`, i `DeleteCommand` właściwości) dla każdej zmianie rekordu w tabeli danych.  
  
> [!NOTE]
>  Jeśli ma wystarczającej ilości informacji w głównym zapytaniu `InsertCommand`, `UpdateCommand`, i `DeleteCommand` poleceń są domyślnie tworzone po wygenerowaniu TableAdapter. Jeśli zapytanietableadapter głównej jest więcej niż jednej tabeli instrukcji SELECT, jest to możliwe, Projektant nie będzie mógł wygenerować `InsertCommand`, `UpdateCommand`, i `DeleteCommand`. Jeśli te polecenia nie są generowane, być może otrzymasz komunikat o błędzie podczas uruchamiania `TableAdapter.Update` metody.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Oprócz `InsertCommand`, `UpdateCommand`, i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które można uruchamiać bezpośrednio w bazie danych. Te metody (`TableAdapter.Insert`, `TableAdapter.Update`, i `TableAdapter.Delete`) może być wywoływany bezpośrednio do manipulowania danymi w bazie danych. Oznacza to, że może wywoływać te poszczególne metody w kodzie zamiast wywoływać metodę `TableAdapter.Update` do obsługi operacji wstawiania, aktualizacji i usuwa oczekujące dla tabeli powiązane dane.  
  
 Jeśli nie chcesz utworzyć te metody bezpośrednie, ustaw TableAdapter **GenerateDbDirectMethods** właściwości `false` (w **właściwości** okno). Dodatkowe zapytania, które są dodawane do elementu TableAdapter są autonomiczne zapytań — nie generują te metody.  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter obsługę typów dopuszczających wartości zerowe  
 TableAdapters obsługuje typy dopuszczające wartości zerowe `Nullable(Of T)` i `T?`. Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku Visual Basic, zobacz [typów wartości dopuszczających wartości zerowe](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Aby uzyskać więcej informacji na temat typów dopuszczających wartości zerowe w języku C#, zobacz [przy użyciu typów dopuszczających wartości zerowe](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="security"></a>Zabezpieczenia  
 Kiedy używasz polecenia danych za pomocą `CommandType` właściwością <xref:System.Data.CommandType>, należy dokładnie sprawdzić informacje przesyłane przez klienta przed przekazaniem go do bazy danych. Złośliwi użytkownicy mogą próby wysłania przez użytkownika (wstrzyknąć) zmodyfikowany lub dodatkowych instrukcji SQL w celu uzyskania nieautoryzowanego dostępu lub uszkodzenia bazy danych. Przed przeniesieniem danych wejściowych użytkownika do bazy danych zawsze sprawdzić, czy informacje są prawidłowe. Najlepszym rozwiązaniem jest zawsze używaj sparametryzowanych zapytań lub procedur przechowywanych, gdy jest to możliwe.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
