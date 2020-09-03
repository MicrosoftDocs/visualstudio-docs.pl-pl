---
title: Wypełnianie zestawów danych za pomocą TableAdapters | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fd1dcf464b7628e345845ca9f371ef6de1efe88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672355"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Wypełnianie zestawów danych za pomocą adapterów TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Składnik TableAdapter wypełnia zestaw danych z danymi z bazy danych, na podstawie jednej lub kilku zapytań lub procedur przechowywanych, które określisz. TableAdapters może również wykonywać operacje dodawania, aktualizacji i usuwania w bazie danych, aby zachować zmiany wprowadzone w zestawie danych. Możesz również wydać polecenia globalne, które nie są powiązane z żadną określoną tabelą.

> [!NOTE]
> TableAdapters są generowane przez projektantów programu Visual Studio. Jeśli tworzysz zestawy danych programowo, użyj elementu DataAdapter, który jest klasą .NET Framework.

 Aby uzyskać szczegółowe informacje o operacjach TableAdapter, możesz przejść bezpośrednio do jednego z następujących tematów:

|Temat|Opis|
|-----------|-----------------|
|[Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Jak używać projektantów do tworzenia i konfigurowania TableAdapters|
|[Tworzenie sparametryzowanych zapytań adaptera TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Jak umożliwić użytkownikom dostarczanie argumentów do procedur lub zapytań TableAdapter|
|[Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Jak używać metod DBDirect TableAdapters|
|[Wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Jak korzystać z ograniczeń klucza obcego podczas aktualizowania danych|
|[Jak zwiększyć funkcjonalność elementu TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Jak dodać niestandardowy kod do TableAdapters|
|[Odczytywanie danych XML do zestawu danych](../data-tools/read-xml-data-into-a-dataset.md)|Jak korzystać z XML|

## <a name="tableadapters-overview"></a>Omówienie adapterów TableAdapter
 TableAdapters to składniki generowane przez projektanta, które łączą się z bazą danych, uruchamiają zapytania lub procedury składowane i wypełniają ich DataTable danymi zwracanymi. TableAdapters również wysyłać zaktualizowane dane z aplikacji z powrotem do bazy danych. Można uruchamiać dowolną liczbę zapytań na TableAdapter, o ile zwracają dane, które są zgodne ze schematem tabeli, z którym jest skojarzona TableAdapter. Na poniższym diagramie pokazano, w jaki sposób TableAdapters współdziałać z bazami danych i innymi obiektami w pamięci:

 ![Przepływ danych w aplikacji klienckiej](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")

 Chociaż TableAdapters są zaprojektowane z **Projektant obiektów DataSet**, klasy TableAdapter nie są generowane jako klasy zagnieżdżone  <xref:System.Data.DataSet> . Znajdują się one w oddzielnych przestrzeniach nazw, które są specyficzne dla każdego zestawu danych. Na przykład, jeśli masz zestaw danych o nazwie `NorthwindDataSet` , TableAdapters, które są skojarzone z  <xref:System.Data.DataTable> s w, `NorthwindDataSet` zostałyby w `NorthwindDataSetTableAdapters` przestrzeni nazw. Aby programowo uzyskać dostęp do określonego TableAdapter, należy zadeklarować nowe wystąpienie TableAdapter. Na przykład:

 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]

## <a name="associated-datatable-schema"></a>Skojarzony schemat DataTable
 Podczas tworzenia TableAdapter należy użyć wstępnego zapytania lub procedury składowanej w celu zdefiniowania schematu skojarzonego elementu TableAdapter <xref:System.Data.DataTable> . To zapytanie początkowe lub procedura składowana jest uruchamiana przez wywołanie metody TableAdapter `Fill` (która wypełnia skojarzone TableAdapter <xref:System.Data.DataTable> ). Wszelkie zmiany wprowadzone w głównym zapytaniu TableAdapter są odzwierciedlane w schemacie skojarzonej tabeli danych. Na przykład usunięcie kolumny z głównego zapytania spowoduje również usunięcie kolumny ze skojarzonej tabeli danych. Jeśli jakiekolwiek dodatkowe zapytania w TableAdapter używają instrukcji SQL, które zwracają kolumny, które nie znajdują się w głównym zapytaniu, Projektant próbuje zsynchronizować zmiany kolumny między głównym pytaniem i dodatkowymi zapytaniami. Aby uzyskać więcej informacji, zobacz [How to: Edit TableAdapters](https://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).

## <a name="tableadapter-update-commands"></a>Polecenia aktualizacji TableAdapter
 Funkcja aktualizacji TableAdapter zależy od ilości dostępnych informacji w głównym zapytaniu w Kreatorze TableAdapter. Na przykład TableAdapters, które są skonfigurowane do pobierania wartości z wielu tabel (sprzężeń), wartości skalarnych, widoków lub wyników funkcji agregujących, nie są początkowo tworzone z możliwością wysyłania aktualizacji z powrotem do źródłowej bazy danych. Można jednak ręcznie skonfigurować polecenia INSERT, UPDATE i DELETE w oknie **Właściwości** .

## <a name="tableadapter-queries"></a>TableAdapter— Zapytania
 ![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif "TableAdapter")

 TableAdapters może zawierać wiele zapytań do wypełnienia skojarzonych tabel danych. Można zdefiniować dowolną liczbę zapytań dla TableAdapter, gdy aplikacja wymaga, o ile każda kwerenda zwraca dane, które są zgodne z tym samym schematem, co skojarzona z nim tabela danych. Ta funkcja umożliwia TableAdapterom ładowanie różnych wyników w oparciu o różne kryteria.

 Jeśli na przykład aplikacja zawiera tabelę z nazwami klientów, można utworzyć zapytanie, które wypełnia tabelę każdą nazwą klienta rozpoczynającą się od określonej litery, a druga wypełnia tabelę wszystkimi klientami, które znajdują się w tym samym stanie. Aby wypełnić `Customers` tabelę z klientami w danym stanie, można utworzyć `FillByState` zapytanie, które pobiera wartość stanu w następujący sposób: `SELECT * FROM Customers WHERE State = @State` . Zapytanie jest uruchamiane przez wywołanie `FillByState` metody i przekazanie wartości parametru w następujący sposób: `CustomerTableAdapter.FillByState("WA")` .

 Oprócz dodawania zapytań, które zwracają dane tego samego schematu co tabela danych TableAdapter, można dodawać zapytania, które zwracają wartości skalarne (pojedyncza). Na przykład zapytanie zwracające liczbę klientów ( `SELECT Count(*) From Customers` ) jest prawidłowe dla, mimo że `CustomersTableAdapter,` zwracane dane nie są zgodne ze schematem tabeli.

## <a name="clearbeforefill-property"></a>Właściwość ClearBeforeFill
 Domyślnie za każdym razem, gdy uruchamiasz zapytanie w celu wypełnienia tabeli danych TableAdapter, istniejące dane są czyszczone i tylko wyniki zapytania są ładowane do tabeli. Ustaw `ClearBeforeFill` Właściwość TableAdapter na, `false` Jeśli chcesz dodać lub scalić dane zwracane z zapytania do istniejących danych w tabeli danych. Bez względu na to, czy wyczyścisz dane, musisz jawnie wysyłać aktualizacje z powrotem do bazy danych, jeśli chcesz je zachować. Pamiętaj, aby zapisać wszelkie zmiany danych w tabeli przed uruchomieniem kolejnego zapytania, które wypełnia tabelę. Aby uzyskać więcej informacji, zobacz [Aktualizowanie danych przy użyciu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Dziedziczenie TableAdapter
 TableAdapters rozszerzyć funkcjonalność standardowych kart danych przez hermetyzację skonfigurowanej <xref:System.Data.Common.DataAdapter> klasy? qualifyHint = False&autoupgrade = true. Domyślnie TableAdapter dziedziczy z <xref:System.ComponentModel.Component> klasy i nie może być rzutowany do <xref:System.Data.Common.DataAdapter> klasy. Rzutowanie elementu TableAdapter na <xref:System.Data.Common.DataAdapter> klasę powoduje <xref:System.InvalidCastException> błąd? QualifyHint = false&autoupgrade = true. Aby zmienić klasę bazową elementu TableAdapter, można wpisać klasę, która dziedziczy z <xref:System.ComponentModel.Component> we właściwości **klasy bazowej** TableAdapter w **Projektant obiektów DataSet**.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter — metody i właściwości
 Klasa TableAdapter nie jest częścią [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Oznacza to, że nie można go znaleźć w dokumentacji ani **Przeglądarka obiektów**. Jest on tworzony w czasie projektowania, gdy używasz jednego z kreatorów wymienionych wcześniej. Nazwa przypisana do TableAdapter podczas tworzenia jest oparta na nazwie tabeli, z którą pracujesz. Na przykład po utworzeniu TableAdapter na podstawie tabeli w bazie danych o nazwie `Orders` TableAdapter ma nazwę `OrdersTableAdapter` . Nazwę klasy TableAdapter można zmienić przy użyciu właściwości **name** w **Projektant obiektów DataSet**.

 Poniżej przedstawiono najczęściej używane metody i właściwości TableAdapters:

|Członek|Opis|
|------------|-----------------|
|`TableAdapter.Fill`|Wypełnia tabelę danych skojarzonych TableAdapter z wynikami polecenia SELECT TableAdapter.|
|`TableAdapter.Update`|Program wysyła zmiany z powrotem do bazy danych i zwraca liczbę całkowitą, która odpowiada liczbie wierszy, na które miała wpływ aktualizacja. Aby uzyskać więcej informacji, zobacz [Aktualizowanie danych przy użyciu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Zwraca nowy <xref:System.Data.DataTable> wypełniony danymi.|
|`TableAdapter.Insert`|Tworzy nowy wiersz w tabeli danych. Aby uzyskać więcej informacji, zobacz [wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Określa, czy tabela danych jest opróżniana przed wywołaniem jednej z `Fill` metod.|

## <a name="tableadapter-update-method"></a>TableAdapter — Metoda aktualizacji
 TableAdapters używać poleceń danych do odczytu i zapisu w bazie danych. Początkowe `Fill` zapytanie TableAdapter (Main) służy jako podstawa do tworzenia schematu powiązanej tabeli danych, `InsertCommand` a także `UpdateCommand` poleceń, i, `DeleteCommand` które są skojarzone z tą `TableAdapter.Update` metodą. Wywołanie `Update` metody TableAdapter uruchamia instrukcje, które zostały utworzone podczas pierwotnego konfigurowania TableAdapter, a nie jedno z dodatkowych zapytań, które zostały dodane za pomocą **Kreatora konfiguracji zapytania TableAdapter**.

 W przypadku korzystania z TableAdapter, efektywnie wykonuje te same operacje z poleceniami, które zwykle można wykonać. Na przykład po wywołaniu `Fill` metody karty Karta uruchamia polecenie dane w swojej `SelectCommand` właściwości i używa czytnika danych (na przykład <xref:System.Data.SqlClient.SqlDataReader> ) do załadowania zestawu wyników do tabeli danych. Podobnie, gdy wywoływana jest metoda adaptera `Update` , uruchamia odpowiednie polecenie (w `UpdateCommand` , `InsertCommand` i `DeleteCommand` Właściwości) dla każdego zmienionego rekordu w tabeli danych.

> [!NOTE]
> Jeśli zapytanie główne zawiera wystarczającą ilość informacji, `InsertCommand` `UpdateCommand` polecenia, i `DeleteCommand` są tworzone domyślnie po wygenerowaniu TableAdapter. Jeśli główne zapytanie TableAdapter jest więcej niż pojedyncza instrukcja SELECT tabeli, możliwe, że projektant nie będzie w stanie generować  `InsertCommand` , `UpdateCommand` i `DeleteCommand` . Jeśli te polecenia nie są generowane, podczas uruchamiania metody może wystąpić błąd `TableAdapter.Update` .

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods
 Oprócz  `InsertCommand` , `UpdateCommand` , i `DeleteCommand` , TableAdapters są tworzone przy użyciu metod, które można uruchamiać bezpośrednio w bazie danych. Te metody ( `TableAdapter.Insert` , `TableAdapter.Update` i `TableAdapter.Delete` ) można wywołać bezpośrednio w celu manipulowania danymi w bazie danych. Oznacza to, że można wywoływać te pojedyncze metody z kodu zamiast wywołania `TableAdapter.Update` do obsługi operacji wstawiania, aktualizacji i usuwania oczekujących dla skojarzonej tabeli danych.

 Jeśli nie chcesz tworzyć tych metod bezpośrednich, ustaw właściwość **GenerateDBDirectMethods** TableAdapter na wartość `false` (w oknie **Właściwości** ). Dodatkowe zapytania dodawane do TableAdapter są zapytania autonomiczne — nie generują tych metod.

## <a name="tableadapter-support-for-nullable-types"></a>Obsługa TableAdapter dla typów dopuszczających wartości null
 TableAdapters obsługują Typy dopuszczające wartości null `Nullable(Of T)` i `T?` . Aby uzyskać więcej informacji na temat typów dopuszczających wartości null w Visual Basic, zobacz [dopuszczanie typów wartości null](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Aby uzyskać więcej informacji na temat typów dopuszczających wartości null w języku C#, zobacz [using nullable Types](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).

## <a name="security"></a>Zabezpieczenia
 Korzystając z poleceń danych z `CommandType` ustawioną właściwością do <xref:System.Data.CommandType> , należy uważnie sprawdzić informacje wysyłane z klienta przed przekazaniem go do bazy danych. Złośliwi użytkownicy mogą próbować wysyłać (wstrzyknąć) zmodyfikowane lub dodatkowe instrukcje SQL w celu uzyskania nieautoryzowanego dostępu lub uszkodzenia bazy danych. Przed przeniesieniem danych wejściowych użytkownika do bazy danych programu należy zawsze sprawdzić, czy informacje są prawidłowe. Najlepszym rozwiązaniem jest zawsze używanie sparametryzowanych zapytań lub procedur składowanych, gdy jest to możliwe.

## <a name="see-also"></a>Zobacz też
 [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
