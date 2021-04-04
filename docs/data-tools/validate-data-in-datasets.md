---
title: Weryfikowanie danych w zestawach danych
description: Dowiedz się, jak weryfikować dane w zestawach danych. Sprawdzanie poprawności danych obejmuje potwierdzenie, że wartości wprowadzone do obiektów danych są zgodne z ograniczeniami w schemacie zestawu danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 82cfcf1ce030cfe597c3ae7bfe85c528184c548a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215672"
---
# <a name="validate-data-in-datasets"></a>Weryfikowanie danych w zestawach danych
Sprawdzanie poprawności danych jest procesem potwierdzającym, że wartości wprowadzane do obiektów danych są zgodne z ograniczeniami w schemacie zestawu danych. Proces weryfikacji potwierdza również, że te wartości są przestrzegane w regułach, które zostały określone dla danej aplikacji. Dobrym sposobem jest zweryfikowanie danych przed wysłaniem aktualizacji do źródłowej bazy danych. Pozwala to zmniejszyć liczbę błędów, a także potencjalne liczby operacji rundy między aplikacją a bazą danych.

Można potwierdzić, że dane, które są zapisywane w zestawie danych, są prawidłowe przez skompilowanie kontroli walidacji do samego zestawu danych. Zestaw danych może sprawdzić dane niezależnie od sposobu wykonywania aktualizacji — bezpośrednio przez kontrolki w formularzu, w składniku lub w inny sposób. Ponieważ zestaw danych jest częścią aplikacji (w przeciwieństwie do zaplecza bazy danych), jest to miejsce logiczne do kompilowania sprawdzania poprawności specyficznej dla aplikacji.

Najlepszym miejscem na dodanie walidacji do aplikacji jest plik klasy częściowej zestawu danych. W programie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Otwórz **Projektant obiektów DataSet** i kliknij dwukrotnie kolumnę lub tabelę, dla której chcesz utworzyć walidację. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> programu obsługi zdarzeń lub.

## <a name="validate-data"></a>Sprawdzanie poprawności danych
Walidacja w zestawie danych jest realizowana w następujący sposób:

- Tworząc własne sprawdzanie poprawności specyficzne dla aplikacji, które mogą sprawdzać wartości w poszczególnych kolumnach danych podczas wprowadzania zmian. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w kolumnie](validate-data-in-datasets.md).

- Tworząc własne sprawdzanie poprawności specyficzne dla aplikacji, które mogą sprawdzać dane do wartości podczas zmiany całego wiersza danych. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w wierszach](validate-data-in-datasets.md).

- Tworząc klucze, unikatowe ograniczenia i tak dalej, jako część rzeczywistej definicji schematu zestawu danych.

- Ustawiając właściwości <xref:System.Data.DataColumn> obiektu, takie jak <xref:System.Data.DataColumn.MaxLength%2A> , <xref:System.Data.DataColumn.AllowDBNull%2A> , i <xref:System.Data.DataColumn.Unique%2A> .

<xref:System.Data.DataTable>Obiekt po wystąpieniu zmiany w rekordzie są wywoływane kilka zdarzeń:

- <xref:System.Data.DataTable.ColumnChanging>Zdarzenia i <xref:System.Data.DataTable.ColumnChanged> są wywoływane podczas każdej zmiany do pojedynczej kolumny. <xref:System.Data.DataTable.ColumnChanging>Zdarzenie jest przydatne, gdy chcesz sprawdzić poprawność zmian w określonych kolumnach. Informacje o proponowanej zmianie są przesyłane jako argument ze zdarzeniem.
- <xref:System.Data.DataTable.RowChanging>Zdarzenia i <xref:System.Data.DataTable.RowChanged> są wywoływane podczas i po każdej zmianie w wierszu. <xref:System.Data.DataTable.RowChanging>To zdarzenie jest bardziej ogólne. Wskazuje, że w wierszu występuje zmiana, ale nie wiesz, która kolumna została zmieniona.

Domyślnie każda zmiana w kolumnie powoduje wypróbowanie czterech zdarzeń. Pierwszy to <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> zdarzenia i dla konkretnej kolumny, która jest zmieniana. Następne są <xref:System.Data.DataTable.RowChanging> zdarzenia i <xref:System.Data.DataTable.RowChanged> . W przypadku wprowadzenia wielu zmian w wierszu zdarzenia zostaną wygenerowane dla każdej zmiany.

> [!NOTE]
> Metoda wiersza danych <xref:System.Data.DataRow.BeginEdit%2A> powoduje wyłączenie <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> zdarzeń i po każdej zmianie poszczególnych kolumn. W takim przypadku zdarzenie nie jest wywoływane do momentu <xref:System.Data.DataRow.EndEdit%2A> wywołania metody, gdy <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> zdarzenia i są wywoływane tylko raz. Aby uzyskać więcej informacji, zobacz Wyłączanie [ograniczeń podczas wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Wybrane zdarzenie zależy od tego, jak Szczegółowa ma być Walidacja. Jeśli ważne jest, aby przechwytywać błąd natychmiast po zmianie kolumny, walidacja kompilacji przy użyciu <xref:System.Data.DataTable.ColumnChanging> zdarzenia. W przeciwnym razie użyj <xref:System.Data.DataTable.RowChanging> zdarzenia, co może spowodować przechwycenie kilku błędów jednocześnie. Ponadto, jeśli dane są strukturalne, dzięki czemu wartość jednej kolumny jest weryfikowana na podstawie zawartości innej kolumny, należy przeprowadzić walidację podczas <xref:System.Data.DataTable.RowChanging> zdarzenia.

Gdy rekordy są aktualizowane, <xref:System.Data.DataTable> obiekt zgłasza zdarzenia, na które można odpowiedzieć, ponieważ zmiany są wykonywane i po wprowadzeniu zmian.

Jeśli aplikacja używa określonego zestawu danych, można utworzyć obsługę zdarzeń o jednoznacznie określonym typie. Spowoduje to dodanie czterech dodatkowych zdarzeń, dla których można utworzyć programy obsługi: `dataTableNameRowChanging` , `dataTableNameRowChanged` , `dataTableNameRowDeleting` i `dataTableNameRowDeleted` . Te typy programów obsługi zdarzeń przekazują argument, który zawiera nazwy kolumn tabeli, które ułatwiają zapisywanie i odczytywanie kodu.

## <a name="data-update-events"></a>Zdarzenia aktualizacji danych

|Zdarzenie|Opis|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Wartość w kolumnie jest zmieniana. Zdarzenie przekazuje wiersz i kolumnę do użytkownika wraz z proponowaną nową wartością.|
|<xref:System.Data.DataTable.ColumnChanged>|Wartość w kolumnie została zmieniona. Zdarzenie przekazuje wiersz i kolumnę do użytkownika wraz z proponowaną wartością.|
|<xref:System.Data.DataTable.RowChanging>|Zmiany wprowadzone w <xref:System.Data.DataRow> obiekcie mają zostać przekazane z powrotem do zestawu danych. Jeśli metoda nie została wywołana <xref:System.Data.DataRow.BeginEdit%2A> , <xref:System.Data.DataTable.RowChanging> zdarzenie jest wywoływane dla każdej zmiany w kolumnie natychmiast po podniesieniu <xref:System.Data.DataTable.ColumnChanging> zdarzenia. Jeśli wywołano <xref:System.Data.DataRow.BeginEdit%2A> przed wprowadzeniem zmian, <xref:System.Data.DataTable.RowChanging> zdarzenie jest zgłaszane tylko w przypadku wywołania <xref:System.Data.DataRow.EndEdit%2A> metody.<br /><br /> Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (zmiany, wstawienia i tak dalej) jest wykonywany.|
|<xref:System.Data.DataTable.RowChanged>|Wiersz został zmieniony. Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (zmiany, wstawienia i tak dalej) jest wykonywany.|
|<xref:System.Data.DataTable.RowDeleting>|Trwa usuwanie wiersza. Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (usuwania) jest wykonywany.|
|<xref:System.Data.DataTable.RowDeleted>|Wiersz został usunięty. Zdarzenie przekazuje wiersz wraz z wartością wskazującą, jaki typ akcji (usuwania) jest wykonywany.|

<xref:System.Data.DataTable.ColumnChanging>Zdarzenia, <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowDeleting> są wywoływane podczas procesu aktualizacji. Możesz użyć tych zdarzeń do walidacji danych lub wykonywania innych typów przetwarzania. Ponieważ aktualizacja jest w toku podczas tych zdarzeń, można ją anulować, zgłaszając wyjątek, co uniemożliwia zakończenie aktualizacji.

<xref:System.Data.DataTable.ColumnChanged> <xref:System.Data.DataTable.RowChanged> <xref:System.Data.DataTable.RowDeleted> Zdarzenia i są zdarzeniami powiadomień, które są zgłaszane po pomyślnym zakończeniu aktualizacji. Te zdarzenia są przydatne, gdy chcesz podejmować dalsze działania w oparciu o pomyślną aktualizację.

## <a name="validate-data-during-column-changes"></a>Sprawdzanie poprawności danych podczas zmiany kolumny

> [!NOTE]
> **Projektant obiektów DataSet** tworzy klasę częściową, w której logika walidacji może zostać dodana do zestawu danych. Wygenerowany przez projektanta zestaw danych nie usuwa ani nie zmienia żadnego kodu w klasie częściowej.

Można sprawdzić poprawność danych po zmianie wartości w kolumnie danych przez odpowiedź na <xref:System.Data.DataTable.ColumnChanging> zdarzenie. Gdy zostanie zgłoszone, to zdarzenie przekazuje argument zdarzenia ( <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> ), który zawiera wartość proponowaną dla bieżącej kolumny. Na podstawie zawartości `e.ProposedValue` można:

- Zaakceptuj proponowaną wartość, nie rób żadnej operacji.

- Odrzuć proponowaną wartość przez ustawienie błędu kolumny ( <xref:System.Data.DataRow.SetColumnError%2A> ) w ramach programu obsługi zdarzeń zmiany kolumny.

- Opcjonalnie można użyć <xref:System.Windows.Forms.ErrorProvider> formantu, aby wyświetlić komunikat o błędzie dla użytkownika. Aby uzyskać więcej informacji, zobacz [składnik ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Walidacja może być również wykonywana podczas <xref:System.Data.DataTable.RowChanging> zdarzenia.

## <a name="validate-data-during-row-changes"></a>Sprawdzanie poprawności danych podczas zmian w wierszach
Można napisać kod, aby sprawdzić, czy każda kolumna, która ma zostać zweryfikowana, zawiera dane, które spełniają wymagania aplikacji. W tym celu należy ustawić kolumnę, aby wskazać, że zawiera błąd, jeśli proponowana wartość jest nieakceptowalna. W poniższych przykładach określono błąd kolumny, gdy `Quantity` kolumna ma wartość 0 lub mniejszą. Procedury obsługi zdarzeń zmiany wiersza powinny wyglądać podobnie do poniższych przykładów.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Aby sprawdzić poprawność danych po zmianie wiersza (Visual Basic)

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń <xref:System.Data.DataTable> w pliku częściowej klasy zestawu danych.

    > [!TIP]
    > Kliknij dwukrotnie po lewej stronie nazwy tabeli, aby utworzyć procedurę obsługi zdarzeń zmiany wiersza. Jeśli klikniesz dwukrotnie nazwę tabeli, możesz ją edytować.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb" id="Snippet3":::

### <a name="to-validate-data-when-a-row-changes-c"></a>Aby sprawdzić poprawność danych po zmianie wiersza (C#)

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie zestawu danych w Projektant obiektów DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje utworzenie pliku częściowej klasy dla <xref:System.Data.DataTable> .

    > [!NOTE]
    > **Projektant obiektów DataSet** nie tworzy automatycznie zdarzenia obsługi dla <xref:System.Data.DataTable.RowChanging> zdarzenia. Musisz utworzyć metodę, aby obsłużyć <xref:System.Data.DataTable.RowChanging> zdarzenie, i uruchomić kod, aby podłączyć zdarzenie do metody inicjacji tabeli.

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
Każdy wiersz w tabeli danych ma <xref:System.Data.DataRow.RowState%2A> Właściwość, która śledzi bieżący stan tego wiersza przy użyciu wartości w <xref:System.Data.DataRowState> wyliczeniu. Można zwrócić zmienione wiersze z zestawu danych lub tabeli danych przez wywołanie `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> . Możesz sprawdzić, czy zmiany istnieją przed wywołaniem, `GetChanges` wywołując <xref:System.Data.DataSet.HasChanges%2A> metodę zestawu danych.

> [!NOTE]
> Po zatwierdzeniu zmian w zestawie danych lub tabeli danych (poprzez wywołanie <xref:System.Data.DataSet.AcceptChanges%2A> metody) `GetChanges` Metoda nie zwraca żadnych danych. Jeśli aplikacja wymaga przetworzenia zmienionych wierszy, należy przetworzyć zmiany przed wywołaniem `AcceptChanges` metody.

Wywołanie <xref:System.Data.DataSet.GetChanges%2A> metody zestawu danych lub tabeli danych zwraca nowy zestaw danych lub tabelę danych, która zawiera tylko rekordy, które zostały zmienione. Jeśli chcesz uzyskać określone rekordy — na przykład tylko nowe rekordy lub tylko zmodyfikowane rekordy, można przekazać wartość z <xref:System.Data.DataRowState> wyliczenia jako parametr do `GetChanges` metody.

Użyj <xref:System.Data.DataRowVersion> wyliczenia, aby uzyskać dostęp do różnych wersji wiersza (na przykład oryginalnych wartości, które znajdowały się w wierszu przed jego przetworzeniem).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Aby pobrać wszystkie zmienione rekordy z zestawu danych

- Wywoływanie <xref:System.Data.DataSet.GetChanges%2A> metody zestawu danych.

     Poniższy przykład tworzy nowy zestaw danych o nazwie `changedRecords` i wypełnia go wszystkimi zmienionymi rekordami z innego zestawu danych o nazwie `dataSet1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet14":::

### <a name="to-get-all-changed-records-from-a-data-table"></a>Aby pobrać wszystkie zmienione rekordy z tabeli danych

- Wywołaj <xref:System.Data.DataTable.GetChanges%2A> metodę elementu DataTable.

     Poniższy przykład tworzy nową tabelę danych o nazwie `changedRecordsTable` i wypełnia ją wszystkimi zmienionymi rekordami z innej tabeli danych o nazwie `dataTable1` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet15":::

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Aby pobrać wszystkie rekordy z określonym stanem wiersza

- Wywołaj `GetChanges` metodę zestawu danych lub tabeli danych i przekaż <xref:System.Data.DataRowState> wartość wyliczenia jako argument.

     Poniższy przykład pokazuje, jak utworzyć nowy zestaw danych o nazwie `addedRecords` i wypełnić go tylko rekordami, które zostały dodane do `dataSet1` zestawu danych.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet16":::

     Poniższy przykład pokazuje, jak zwrócić wszystkie rekordy, które zostały ostatnio dodane do `Customers` tabeli:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet17":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet17":::

## <a name="access-the-original-version-of-a-datarow"></a>Dostęp do oryginalnej wersji elementu DataRow
Gdy zmiany są wprowadzane do wierszy danych, zestaw danych zachowuje zarówno oryginalną ( <xref:System.Data.DataRowVersion.Original> ), jak i nowe <xref:System.Data.DataRowVersion.Current> wersje wiersza. Na przykład przed wywołaniem `AcceptChanges` metody aplikacja może uzyskać dostęp do różnych wersji rekordu (zgodnie z definicją w <xref:System.Data.DataRowVersion> wyliczeniu) i odpowiednio przetworzyć zmiany.

> [!NOTE]
> Różne wersje wiersza istnieją tylko po jego edytowaniu i przed `AcceptChanges` wywołaniem metody. Po `AcceptChanges` wywołaniu metody bieżące i oryginalne wersje są takie same.

Przekazanie <xref:System.Data.DataRowVersion> wartości wraz z indeksem kolumny (lub nazwą kolumny jako ciągiem) zwraca wartość z określonej w wierszu wersji wiersza. Zmieniona kolumna zostanie zidentyfikowana podczas <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzeń. Jest to dobry moment, aby sprawdzić różne wersje wierszy do celów weryfikacji. Jednak jeśli ograniczenia są tymczasowo zawieszone, te zdarzenia nie zostaną wywołane i będzie trzeba programowo identyfikować kolumny, które uległy zmianie. Można to zrobić przez iterację <xref:System.Data.DataTable.Columns%2A> kolekcji i porównanie różnych <xref:System.Data.DataRowVersion> wartości.

### <a name="to-get-the-original-version-of-a-record"></a>Aby uzyskać oryginalną wersję rekordu

- Uzyskaj dostęp do wartości kolumny, przekazując w <xref:System.Data.DataRowVersion> wierszu, który ma zostać zwrócony.

     Poniższy przykład pokazuje, jak użyć wartości, <xref:System.Data.DataRowVersion> Aby uzyskać oryginalną wartość `CompanyName` pola w <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet21":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet21":::

## <a name="access-the-current-version-of-a-datarow"></a>Dostęp do bieżącej wersji elementu DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Aby pobrać bieżącą wersję rekordu

- Uzyskaj dostęp do wartości kolumny, a następnie Dodaj do indeksu parametr wskazujący, która wersja wiersza ma zostać zwrócona.

     Poniższy przykład pokazuje, jak użyć wartości, <xref:System.Data.DataRowVersion> Aby uzyskać bieżącą wartość `CompanyName` pola w <xref:System.Data.DataRow> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet22":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet22":::

## <a name="see-also"></a>Zobacz też

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Instrukcje: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Instrukcje: wyświetlanie ikon błędów dla walidacji formularza za pomocą składnika Windows Forms ErrorProvider](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
