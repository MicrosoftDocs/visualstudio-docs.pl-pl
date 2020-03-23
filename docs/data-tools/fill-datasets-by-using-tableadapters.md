---
title: Wypełnianie zestawów danych za pomocą adapterów TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302239"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Wypełnianie zestawów danych za pomocą adapterów TableAdapter

Składnik TableAdapter wypełnia zestaw danych danymi z bazy danych na podstawie jednego lub kilku zapytań lub procedur przechowywanych, które określisz. TableAdapters można również wykonywać dodaje, aktualizacje i usuwa w bazie danych, aby utrwalić zmiany wprowadzone do zestawu danych. Można również wydawać polecenia globalne, które nie są związane z dowolną określoną tabelą.

> [!NOTE]
> TableAdapters są generowane przez projektantów programu Visual Studio. Jeśli tworzysz zestawy danych programowo, użyj DataAdapter, który jest klasą .NET.

Aby uzyskać szczegółowe informacje na temat operacji TableAdapter, można przejść bezpośrednio do jednego z następujących tematów:

|Temat|Opis|
|-----------|-----------------|
|[Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)|Jak używać projektantów do tworzenia i konfigurowania tableadapters|
|[Tworzenie sparametryzowanych zapytań adaptera TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Jak umożliwić użytkownikom dostarczanie argumentów do procedur tableadapter lub kwerend|
|[Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Jak korzystać z metod Dbdirect TableAdapters|
|[Wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Jak pracować z ograniczeniami klucza obcego podczas aktualizowania danych|
|[Jak rozszerzyć funkcjonalność tableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Jak dodać kod niestandardowy do TableAdapters|
|[Odczytywanie danych XML do zestawu danych](../data-tools/read-xml-data-into-a-dataset.md)|Jak pracować z XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Omówienie tabeliAdapter

TableAdapters są składnikami generowanymi przez projektanta, które łączą się z bazą danych, uruchamiają kwerendy lub procedury przechowywane i wypełniają ich DataTable zwróconymi danymi. TableAdapters również wysłać zaktualizowane dane z aplikacji z powrotem do bazy danych. Można uruchomić dowolną liczbę zapytań na TableAdapter tak długo, jak zwracają dane, które są zgodne ze schematem tabeli, z którą tableAdapter jest skojarzony. Na poniższym diagramie pokazano, jak TableAdapters interakcji z bazami danych i innymi obiektami w pamięci:

![Przepływ danych w aplikacji klienckiej](../data-tools/media/clientdatadiagram.gif)

Podczas gdy tableadapters są zaprojektowane z **projektantem zestawu danych,** TableAdapter <xref:System.Data.DataSet>klasy nie są generowane jako zagnieżdżone klasy . Znajdują się one w oddzielnych przestrzeniach nazw, które są specyficzne dla każdego zestawu danych. Na przykład jeśli masz zestaw `NorthwindDataSet`danych o nazwie , TableAdapters, które są skojarzone z <xref:System.Data.DataTable>s w `NorthwindDataSet` obszarze `NorthwindDataSetTableAdapters` nazw będzie w obszarze nazw. Aby uzyskać dostęp do określonego TableAdapter programowo, należy zadeklarować nowe wystąpienie TableAdapter. Przykład:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Schemat Skojarzonej tabeli datatable

Podczas tworzenia tableAdapter, należy użyć kwerendy początkowej lub procedury składowanej do definiowania <xref:System.Data.DataTable>schematu TableAdapter skojarzone . Uruchom tę kwerendę początkową lub procedurę składowaną, `Fill` wywołując metodę TableAdapter (która wypełnia <xref:System.Data.DataTable>skojarzoną z tableadapter). Wszelkie zmiany wprowadzone do głównego zapytania TableAdapter są odzwierciedlane w schemacie skojarzonej tabeli danych. Na przykład usunięcie kolumny z kwerendy głównej powoduje również usunięcie kolumny ze skojarzonej tabeli danych. Jeśli wszelkie dodatkowe kwerendy na TableAdapter używać instrukcji SQL, które zwracają kolumny, które nie są w kwerendzie głównej, projektant próbuje zsynchronizować zmiany kolumny między kwerendą główną i dodatkowych zapytań.

## <a name="tableadapter-update-commands"></a>Polecenia aktualizacji tableAdapter

Funkcja aktualizacji tableAdapter zależy od ilości informacji dostępnych w kwerendzie głównej **kreatora tableadapter**. Na przykład TableAdapters, które są skonfigurowane do pobierania `JOIN`wartości z wielu tabel (przy użyciu ), wartości skalarne, widoki lub wyniki funkcji agregujących nie są początkowo tworzone z możliwością wysyłania aktualizacji z powrotem do podstawowej bazy danych. Można jednak ręcznie `INSERT`skonfigurować `UPDATE`polecenie `DELETE` , i polecenia w oknie **Właściwości.**

## <a name="tableadapter-queries"></a>TableAdapter— Zapytania

![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif)

TableAdapters może zawierać wiele zapytań, aby wypełnić ich tabele skojarzonych danych. Można zdefiniować tyle zapytań dla TableAdapter, jak aplikacja wymaga, tak długo, jak każda kwerenda zwraca dane, które są zgodne z tym samym schematem, co skojarzona z nią tabela danych. Ta funkcja umożliwia TableAdapter załadować różne wyniki na podstawie różnych kryteriów.

Na przykład jeśli aplikacja zawiera tabelę z nazwami klientów, można utworzyć kwerendę, która wypełnia tabelę z każdej nazwy klienta, która zaczyna się od określonej litery i inny, który wypełnia tabelę wszystkich klientów, które znajdują się w tym samym stanie. Aby wypełnić tabelę `Customers` klientami w danym `FillByState` stanie, można utworzyć kwerendę, która `SELECT * FROM Customers WHERE State = @State`przyjmuje parametr dla wartości stanu w następujący sposób: . Uruchamiasz kwerendę, `FillByState` wywołując metodę i przekazując w `CustomerTableAdapter.FillByState("WA")`wartości parametru w ten sposób: .

Oprócz dodawania kwerend, które zwracają dane tego samego schematu co tableadapter danych table, można dodać kwerendy, które zwracają wartości skalarne (pojedyncze). Na przykład kwerenda, która zwraca`SELECT Count(*) From Customers`liczbę klientów ( `CustomersTableAdapter,` ) jest prawidłowa dla, nawet jeśli zwracane dane nie są zgodne ze schematem tabeli.

## <a name="clearbeforefill-property"></a>ClearBeforeFill, właściwość

Domyślnie za każdym razem, gdy uruchamiasz kwerendę w celu wypełnienia tabeli danych TableAdapter, istniejące dane są czyszczone, a tylko wyniki kwerendy są ładowane do tabeli. Ustaw TableAdapter `ClearBeforeFill` właściwości, `false` jeśli chcesz dodać lub scalić dane, które są zwracane z kwerendy do istniejących danych w tabeli danych. Niezależnie od tego, czy wyczyścisz dane, należy jawnie wysyłać aktualizacje z powrotem do bazy danych, jeśli chcesz je utrwalić. Dlatego pamiętaj, aby zapisać wszelkie zmiany w danych w tabeli przed uruchomieniem innej kwerendy, która wypełnia tabelę. Aby uzyskać więcej informacji, zobacz [Aktualizowanie danych przy użyciu tableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Dziedzictwo tableAdapter

TableAdapters rozszerzyć funkcjonalność standardowych kart danych przez hermetyzowanie <xref:System.Data.Common.DataAdapter> skonfigurowanej klasy. Domyślnie TableAdapter dziedziczy z <xref:System.ComponentModel.Component> klasy i nie można <xref:System.Data.Common.DataAdapter> rzutować do klasy. Rzutowanie TableAdapter <xref:System.Data.Common.DataAdapter> do klasy <xref:System.InvalidCastException> powoduje błąd. Aby zmienić klasę podstawową tableadapter, można określić <xref:System.ComponentModel.Component> klasę, która wywodzi się z właściwości **Klasa podstawowa** TableAdapter w **Projektancie zestawu danych**.

## <a name="tableadapter-methods-and-properties"></a>Metody i właściwości tableAdapter

Klasa TableAdapter nie jest typem .NET. Oznacza to, że nie można go wyszukać w dokumentacji ani w **przeglądarce obiektów.** Jest tworzony w czasie projektowania, gdy używasz jednego z kreatorów wymienionych wcześniej. Nazwa, która jest przypisana do TableAdapter podczas tworzenia jest oparta na nazwie tabeli, z którą pracujesz. Na przykład podczas tworzenia TableAdapter na podstawie tabeli `Orders`w bazie danych o `OrdersTableAdapter`nazwie , TableAdapter ma nazwę . Nazwę klasy tableAdapter można zmienić za pomocą **Name** właściwości w **Projektancie zestawu danych**.

Poniżej znajdują się powszechnie stosowane metody i właściwości TableAdapters:

|Członek|Opis|
|------------|-----------------|
|`TableAdapter.Fill`|Wypełnia table danych związanych TableAdapter z wynikami TableAdapter `SELECT` polecenia.|
|`TableAdapter.Update`|Wysyła zmiany z powrotem do bazy danych i zwraca liczbę całkowitą, która reprezentuje liczbę wierszy, których dotyczy aktualizacja. Aby uzyskać więcej informacji, zobacz [Aktualizowanie danych przy użyciu tableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Zwraca nowy, <xref:System.Data.DataTable> który jest wypełniony danymi.|
|`TableAdapter.Insert`|Tworzy nowy wiersz w tabeli danych. Aby uzyskać więcej informacji, zobacz [Wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Określa, czy tabela danych jest opróżniany `Fill` przed wywołaniem jednej z metod.|

## <a name="tableadapter-update-method"></a>Metoda aktualizacji TableAdapter

TableAdapters używać poleceń danych do odczytu i zapisu z bazy danych. Użyj tableAdapter początkowej `Fill` (głównej) kwerendy jako podstawy do tworzenia schematu skojarzonej tabeli `InsertCommand` `UpdateCommand`danych, `DeleteCommand` a także , i `TableAdapter.Update` polecenia, które są skojarzone z metodą. Wywołanie `Update` metody TableAdapter uruchamia instrukcje, które zostały utworzone, gdy TableAdapter został pierwotnie skonfigurowany, a nie jeden z dodatkowych zapytań dodanych za pomocą **Kreatora konfiguracji kwerendy TableAdapter**.

Podczas korzystania z TableAdapter, skutecznie wykonuje te same operacje z poleceniami, które zazwyczaj wykonywane. Na przykład podczas wywoływania `Fill` metody karty, karta uruchamia polecenie `SelectCommand` danych we właściwości i używa czytnika danych (na przykład <xref:System.Data.SqlClient.SqlDataReader>), aby załadować zestaw wyników do tabeli danych. Podobnie po `Update` wywołaniu metody karty uruchamia odpowiednie polecenie (w `UpdateCommand`, `InsertCommand`i `DeleteCommand` właściwości) dla każdego zmienionego rekordu w tabeli danych.

> [!NOTE]
> Jeśli w kwerendzie głównej jest `InsertCommand`wystarczająco `UpdateCommand`dużo `DeleteCommand` informacji, polecenia , i polecenia są tworzone domyślnie podczas generowania programu TableAdapter. Jeśli główne zapytanie TableAdapter jest więcej `SELECT` niż jedną instrukcją tabeli, możliwe, że `InsertCommand` `UpdateCommand`projektant `DeleteCommand`nie będzie mógł wygenerować , i . Jeśli te polecenia nie są generowane, może pojawić `TableAdapter.Update` się błąd podczas uruchamiania metody.

## <a name="tableadapter-generatedbdirectmethods"></a>Metody generowania przez programy dbdirect

Oprócz `InsertCommand`, `UpdateCommand`i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które można uruchomić bezpośrednio w bazie danych. Można wywołać te`TableAdapter.Insert` `TableAdapter.Update`metody `TableAdapter.Delete`( , i ) bezpośrednio do manipulowania danymi w bazie danych. Oznacza to, że można wywołać te indywidualne `TableAdapter.Update` metody z kodu zamiast wywoływania do obsługi wstawia, aktualizacje i usuwa, które oczekują na skojarzonej tabeli danych.

Jeśli nie chcesz tworzyć tych metod bezpośrednich, ustaw TableAdapter **GenerateDbDirectMethods** właściwość `false` (w oknie **Właściwości).** Dodatkowe zapytania, które są dodawane do TableAdapter są autonomiczne kwerendy — nie generują tych metod.

## <a name="tableadapter-support-for-nullable-types"></a>Obsługa tableadapter dla typów nullable

TableAdapters obsługują `Nullable(Of T)` typy `T?`nullable i . Aby uzyskać więcej informacji na temat typów nullable w języku Visual Basic, zobacz [Typy wartości nullable](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Aby uzyskać więcej informacji na temat typów nullable w języku C#, zobacz [Użyj typów nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Odwołanie do tableadaptermanager

Domyślnie TableAdapterManager klasa generuje podczas tworzenia zestawu danych, który zawiera tabele pokrewne. Aby zapobiec generowaniu klasy, zmień wartość `Hierarchical Update` właściwości zestawu danych na false. Podczas przeciągania tabeli, która ma relację na powierzchni projektowej formularza systemu Windows lub WPF strony, Visual Studio deklaruje zmienną elementu członkowskiego klasy. Jeśli nie używasz databinding, należy ręcznie zadeklarować zmienną.

Klasa TableAdapterManager nie jest typem .NET. W związku z tym nie można wyszukać go w dokumentacji. Jest tworzony w czasie projektowania w ramach procesu tworzenia zestawu danych.

Poniżej przedstawiono często używane metody i `TableAdapterManager` właściwości klasy:

|Członek|Opis|
|------------|-----------------|
|Metoda `UpdateAll`|Zapisuje wszystkie dane ze wszystkich tabel danych.|
|`BackUpDataSetBeforeUpdate`Właściwość|Określa, czy utworzyć kopię zapasową zestawu danych `TableAdapterManager.UpdateAll` przed wykonaniem metody. Boolean.|
|*właściwość nazwami tableName* `TableAdapter`|Reprezentuje TableAdapter. Wygenerowany TableAdapterManager zawiera właściwość dla każdego `TableAdapter` zarządza. Na przykład zestaw danych z tabelą Klienci i zamówienia generuje z TableAdapterManager, który zawiera `CustomersTableAdapter` i `OrdersTableAdapter` właściwości.|
|`UpdateOrder`Właściwość|Steruje kolejnością poszczególnych poleceń wstawiania, aktualizowania i usuwania. Ustaw to na jedną z `TableAdapterManager.UpdateOrderOption` wartości w wyliczeniu.<br /><br /> Domyślnie jest `UpdateOrder` ustawiona na **InsertUpdateDelete**. Oznacza to, że wstawia, a następnie aktualizacje, a następnie usuwa są wykonywane dla wszystkich tabel w zestawie danych.|

## <a name="security"></a>Zabezpieczenia

Podczas korzystania z poleceń danych z <xref:System.Data.CommandType.Text>CommandType właściwość ustawiona na , dokładnie sprawdzić informacje, które są wysyłane z klienta przed przekazaniem go do bazy danych. Złośliwi użytkownicy mogą próbować wysłać (wstrzyknąć) zmodyfikowane lub dodatkowe instrukcje SQL w celu uzyskania nieautoryzowanego dostępu lub uszkodzenia bazy danych. Przed przeniesieniem danych wejściowych użytkownika do bazy danych należy zawsze sprawdzić, czy informacje są prawidłowe. Najlepszym rozwiązaniem jest zawsze używać sparametryzowanych zapytań lub procedur przechowywanych, gdy jest to możliwe.

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi zestawów danych](../data-tools/dataset-tools-in-visual-studio.md)
