---
title: Weryfikowanie danych w zestawach danych
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed115e851e9c2291dfc9d00f4bb36f670a7f3e00
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586071"
---
# <a name="validate-data-in-datasets"></a>Weryfikowanie danych w zestawach danych
Sprawdzanie poprawności danych jest procesem potwierdzającym, że wartości wprowadzane do obiektów danych są zgodne z ograniczeniami w schemacie zestawu danych. Proces weryfikacji potwierdza również, że te wartości są przestrzegane w regułach, które zostały określone dla danej aplikacji. Dobrym sposobem jest zweryfikowanie danych przed wysłaniem aktualizacji do źródłowej bazy danych. Pozwala to zmniejszyć liczbę błędów, a także potencjalne liczby operacji rundy między aplikacją a bazą danych.

Można potwierdzić, że dane, które są zapisywane w zestawie danych, są prawidłowe przez skompilowanie kontroli walidacji do samego zestawu danych. Zestaw danych może sprawdzić dane niezależnie od sposobu wykonywania aktualizacji — bezpośrednio przez kontrolki w formularzu, w składniku lub w inny sposób. Ponieważ zestaw danych jest częścią aplikacji (w przeciwieństwie do zaplecza bazy danych), jest to miejsce logiczne do kompilowania sprawdzania poprawności specyficznej dla aplikacji.

Najlepszym miejscem na dodanie walidacji do aplikacji jest plik klasy częściowej zestawu danych. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Otwórz **Projektant obiektów DataSet** i kliknij dwukrotnie kolumnę lub tabelę, dla której chcesz utworzyć walidację. Ta akcja powoduje automatyczne utworzenie programu obsługi zdarzeń <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data"></a>Sprawdzanie poprawności danych
Walidacja w zestawie danych jest realizowana w następujący sposób:

- Tworząc własne sprawdzanie poprawności specyficzne dla aplikacji, które mogą sprawdzać wartości w poszczególnych kolumnach danych podczas wprowadzania zmian. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w kolumnie](validate-data-in-datasets.md).

- Tworząc własne sprawdzanie poprawności specyficzne dla aplikacji, które mogą sprawdzać dane do wartości podczas zmiany całego wiersza danych. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w wierszach](validate-data-in-datasets.md).

- Tworząc klucze, unikatowe ograniczenia i tak dalej, jako część rzeczywistej definicji schematu zestawu danych.

- Przez ustawienie właściwości obiektu <xref:System.Data.DataColumn>, takich jak <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>i <xref:System.Data.DataColumn.Unique%2A>.

Obiekt <xref:System.Data.DataTable> zgłasza kilka zdarzeń, gdy w rekordzie występuje zmiana:

- Zdarzenia <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> są wywoływane podczas i po każdej zmianie w pojedynczej kolumnie. Zdarzenie <xref:System.Data.DataTable.ColumnChanging> jest przydatne, gdy chcesz sprawdzić poprawność zmian w określonych kolumnach. Informacje o proponowanej zmianie są przesyłane jako argument ze zdarzeniem.
- Zdarzenia <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> są wywoływane podczas i po każdej zmianie w wierszu. <xref:System.Data.DataTable.RowChanging> zdarzenie jest bardziej ogólne. Wskazuje, że w wierszu występuje zmiana, ale nie wiesz, która kolumna została zmieniona.

Domyślnie każda zmiana w kolumnie powoduje wypróbowanie czterech zdarzeń. Pierwszy to <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia dla konkretnej kolumny, która jest zmieniana. Poniżej znajdują się zdarzenia <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged>. W przypadku wprowadzenia wielu zmian w wierszu zdarzenia zostaną wygenerowane dla każdej zmiany.

> [!NOTE]
> Metoda <xref:System.Data.DataRow.BeginEdit%2A> wiersza danych wyłącza zdarzenia <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> po zmianie poszczególnych kolumn. W takim przypadku zdarzenie nie jest wywoływane do momentu wywołania metody <xref:System.Data.DataRow.EndEdit%2A>, gdy zdarzenia <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> są zgłaszane tylko raz. Aby uzyskać więcej informacji, zobacz Wyłączanie [ograniczeń podczas wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Wybrane zdarzenie zależy od tego, jak Szczegółowa ma być Walidacja. Jeśli ważne jest, aby przechwytywać błąd natychmiast po zmianie kolumny, walidacja kompilacji przy użyciu zdarzenia <xref:System.Data.DataTable.ColumnChanging>. W przeciwnym razie użyj zdarzenia <xref:System.Data.DataTable.RowChanging>, co może spowodować przechwycenie kilku błędów jednocześnie. Ponadto, jeśli dane są strukturalne, więc wartość jednej kolumny jest sprawdzana na podstawie zawartości innej kolumny, należy przeprowadzić walidację podczas zdarzenia <xref:System.Data.DataTable.RowChanging>.

Gdy rekordy są aktualizowane, obiekt <xref:System.Data.DataTable> zgłasza zdarzenia, na które można odpowiedzieć, ponieważ zmiany są wykonywane i po wprowadzeniu zmian.

Jeśli aplikacja używa określonego zestawu danych, można utworzyć obsługę zdarzeń o jednoznacznie określonym typie. Spowoduje to dodanie czterech dodatkowych zdarzeń z określonym typem, dla których można tworzyć programy obsługi: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`i `dataTableNameRowDeleted`. Te typy programów obsługi zdarzeń przekazują argument, który zawiera nazwy kolumn tabeli, które ułatwiają zapisywanie i odczytywanie kodu.

## <a name="data-update-events"></a>Zdarzenia aktualizacji danych

|Zdarzenie|Opis|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Wartość w kolumnie jest zmieniana. Zdarzenie przekazuje wiersz i kolumnę do użytkownika wraz z proponowaną nową wartością.|
|<xref:System.Data.DataTable.ColumnChanged>|Wartość w kolumnie została zmieniona. Zdarzenie przekazuje wiersz i kolumnę do użytkownika wraz z proponowaną wartością.|
|<xref:System.Data.DataTable.RowChanging>|Zmiany wprowadzone w obiekcie <xref:System.Data.DataRow> zostaną zatwierdzone z powrotem do zestawu danych. Jeśli metoda <xref:System.Data.DataRow.BeginEdit%2A> nie została wywołana, zdarzenie <xref:System.Data.DataTable.RowChanging> jest zgłaszane dla każdej zmiany w kolumnie natychmiast po podniesieniu zdarzenia <xref:System.Data.DataTable.ColumnChanging>. Jeśli przed wprowadzeniem zmian wywołano <xref:System.Data.DataRow.BeginEdit%2A>, zdarzenie <xref:System.Data.DataTable.RowChanging> zostanie wywołane tylko po wywołaniu metody <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (zmiany, wstawienia i tak dalej) jest wykonywany.|
|<xref:System.Data.DataTable.RowChanged>|Wiersz został zmieniony. Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (zmiany, wstawienia i tak dalej) jest wykonywany.|
|<xref:System.Data.DataTable.RowDeleting>|Trwa usuwanie wiersza. Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (usuwania) jest wykonywany.|
|<xref:System.Data.DataTable.RowDeleted>|Wiersz został usunięty. Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (usuwania) jest wykonywany.|

Zdarzenia <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>i <xref:System.Data.DataTable.RowDeleting> są wywoływane podczas procesu aktualizacji. Możesz użyć tych zdarzeń do walidacji danych lub wykonywania innych typów przetwarzania. Ponieważ aktualizacja jest w toku podczas tych zdarzeń, można ją anulować, zgłaszając wyjątek, co uniemożliwia zakończenie aktualizacji.

Zdarzenia <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> i <xref:System.Data.DataTable.RowDeleted> są zdarzeniami powiadomień, które są zgłaszane po pomyślnym zakończeniu aktualizacji. Te zdarzenia są przydatne, gdy chcesz podejmować dalsze działania w oparciu o pomyślną aktualizację.

## <a name="validate-data-during-column-changes"></a>Sprawdzanie poprawności danych podczas zmiany kolumny

> [!NOTE]
> **Projektant obiektów DataSet** tworzy klasę częściową, w której logika walidacji może zostać dodana do zestawu danych. Wygenerowany przez projektanta zestaw danych nie usuwa ani nie zmienia żadnego kodu w klasie częściowej.

Możesz sprawdzić poprawność danych, gdy wartość w kolumnie danych ulegnie zmianie, reagując na zdarzenie <xref:System.Data.DataTable.ColumnChanging>. Gdy zostanie zgłoszone, to zdarzenie przekazuje argument zdarzenia (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>), który zawiera wartość proponowaną dla bieżącej kolumny. Na podstawie zawartości `e.ProposedValue`można:

- Zaakceptuj proponowaną wartość, nie rób żadnej operacji.

- Odrzuć proponowaną wartość przez ustawienie błędu kolumny (<xref:System.Data.DataRow.SetColumnError%2A>) z procedury obsługi zdarzeń zmieniającej kolumny.

- Opcjonalnie można użyć formantu <xref:System.Windows.Forms.ErrorProvider>, aby wyświetlić komunikat o błędzie dla użytkownika. Aby uzyskać więcej informacji, zobacz [składnik ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Walidację można także wykonać podczas zdarzenia <xref:System.Data.DataTable.RowChanging>.

## <a name="validate-data-during-row-changes"></a>Sprawdzanie poprawności danych podczas zmian w wierszach
Można napisać kod, aby sprawdzić, czy każda kolumna, która ma zostać zweryfikowana, zawiera dane, które spełniają wymagania aplikacji. W tym celu należy ustawić kolumnę, aby wskazać, że zawiera błąd, jeśli proponowana wartość jest nieakceptowalna. W poniższych przykładach określono błąd kolumny, gdy kolumna `Quantity` ma wartość 0 lub mniejszą. Procedury obsługi zdarzeń zmiany wiersza powinny wyglądać podobnie do poniższych przykładów.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Aby sprawdzić poprawność danych po zmianie wiersza (Visual Basic)

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje automatyczne utworzenie procedury obsługi zdarzeń <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable> w pliku częściowej klasy zestawu danych.

    > [!TIP]
    > Kliknij dwukrotnie po lewej stronie nazwy tabeli, aby utworzyć procedurę obsługi zdarzeń zmiany wiersza. Jeśli klikniesz dwukrotnie nazwę tabeli, możesz ją edytować.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Aby sprawdzić poprawność danych po zmianieC#wiersza ()

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje utworzenie pliku częściowej klasy dla <xref:System.Data.DataTable>.

    > [!NOTE]
    > **Projektant obiektów DataSet** nie tworzy automatycznie obsługi zdarzeń dla zdarzenia <xref:System.Data.DataTable.RowChanging>. Musisz utworzyć metodę do obsługi zdarzenia <xref:System.Data.DataTable.RowChanging> i uruchomić kod, aby podłączyć zdarzenie do metody inicjacji tabeli.

3. Skopiuj następujący kod do klasy częściowej:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>Aby pobrać zmienione wiersze
Każdy wiersz w tabeli danych ma właściwość <xref:System.Data.DataRow.RowState%2A>, która śledzi bieżący stan tego wiersza przy użyciu wartości w <xref:System.Data.DataRowState> wyliczenia. Można zwrócić zmienione wiersze z zestawu danych lub tabeli danych, wywołując metodę `GetChanges` <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>. Przed wywołaniem `GetChanges` można sprawdzić, czy istnieją zmiany, wywołując metodę <xref:System.Data.DataSet.HasChanges%2A> zestawu danych.

> [!NOTE]
> Po zatwierdzeniu zmian w zestawie danych lub tabeli danych (poprzez wywołanie metody <xref:System.Data.DataSet.AcceptChanges%2A>) Metoda `GetChanges` nie zwraca żadnych danych. Jeśli aplikacja wymaga przetworzenia zmienionych wierszy, należy przetworzyć zmiany przed wywołaniem metody `AcceptChanges`.

Wywołanie metody <xref:System.Data.DataSet.GetChanges%2A> zestawu danych lub tabeli danych zwraca nowy zestaw danych lub tabelę danych, która zawiera tylko rekordy, które zostały zmienione. Jeśli chcesz uzyskać określone rekordy — na przykład tylko nowe rekordy lub tylko zmodyfikowane rekordy — można przekazać wartość z wyliczenia <xref:System.Data.DataRowState> jako parametr do metody `GetChanges`.

Użyj wyliczenia <xref:System.Data.DataRowVersion>, aby uzyskać dostęp do różnych wersji wiersza (na przykład oryginalnych wartości, które znajdowały się w wierszu przed jego przetworzeniem).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Aby pobrać wszystkie zmienione rekordy z zestawu danych

- Wywołaj metodę <xref:System.Data.DataSet.GetChanges%2A> zestawu danych.

     Poniższy przykład tworzy nowy zestaw danych o nazwie `changedRecords` i wypełnia go wszystkimi zmienionymi rekordami z innego zestawu danych o nazwie `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Aby pobrać wszystkie zmienione rekordy z tabeli danych

- Wywołaj metodę <xref:System.Data.DataTable.GetChanges%2A> obiektu DataTable.

     Poniższy przykład tworzy nową tabelę danych o nazwie `changedRecordsTable` i wypełnia ją wszystkimi zmienionymi rekordami z innej tabeli danych o nazwie `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Aby pobrać wszystkie rekordy z określonym stanem wiersza

- Wywołaj metodę `GetChanges` zestawu danych lub tabeli danych i przekaż <xref:System.Data.DataRowState> wartość wyliczenia jako argument.

     Poniższy przykład pokazuje, jak utworzyć nowy zestaw danych o nazwie `addedRecords` i wypełnić go tylko rekordami, które zostały dodane do `dataSet1` zestawu danych.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Poniższy przykład pokazuje, jak zwrócić wszystkie rekordy, które zostały ostatnio dodane do tabeli `Customers`:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Dostęp do oryginalnej wersji elementu DataRow
Gdy zmiany są wprowadzane do wierszy danych, zestaw danych zachowuje zarówno oryginalną (<xref:System.Data.DataRowVersion.Original>), jak i wersje nowych (<xref:System.Data.DataRowVersion.Current>) wiersza. Na przykład przed wywołaniem metody `AcceptChanges` aplikacja może uzyskać dostęp do różnych wersji rekordu (zgodnie z definicją w <xref:System.Data.DataRowVersion> Enumeration) i odpowiednio przetworzyć zmiany.

> [!NOTE]
> Różne wersje wiersza istnieją tylko po jego edytowaniu i przed wywołaniem metody `AcceptChanges`. Po wywołaniu metody `AcceptChanges` bieżąca i oryginalna wersja są takie same.

Przekazywanie wartości <xref:System.Data.DataRowVersion> wraz z indeksem kolumny (lub nazwą kolumny jako ciągiem) zwraca wartość z określonej w wierszu wersji wiersza. Zmieniona kolumna zostanie zidentyfikowana podczas zdarzeń <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged>. Jest to dobry moment, aby sprawdzić różne wersje wierszy do celów weryfikacji. Jednak jeśli ograniczenia są tymczasowo zawieszone, te zdarzenia nie zostaną wywołane i będzie trzeba programowo identyfikować kolumny, które uległy zmianie. Można to zrobić przez iterację kolekcji <xref:System.Data.DataTable.Columns%2A> i porównanie różnych wartości <xref:System.Data.DataRowVersion>.

### <a name="to-get-the-original-version-of-a-record"></a>Aby uzyskać oryginalną wersję rekordu

- Dostęp do wartości kolumny przez przekazanie <xref:System.Data.DataRowVersion> wiersza, który ma zostać zwrócony.

     Poniższy przykład pokazuje, jak używać wartości <xref:System.Data.DataRowVersion>, aby uzyskać oryginalną wartość pola `CompanyName` w <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Dostęp do bieżącej wersji elementu DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Aby pobrać bieżącą wersję rekordu

- Uzyskaj dostęp do wartości kolumny, a następnie Dodaj do indeksu parametr wskazujący, która wersja wiersza ma zostać zwrócona.

     Poniższy przykład pokazuje, jak używać wartości <xref:System.Data.DataRowVersion>, aby uzyskać bieżącą wartość pola `CompanyName` w <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Instrukcje: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Instrukcje: wyświetlanie ikon błędów dla walidacji formularza za pomocą składnika Windows Forms ErrorProvider](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
