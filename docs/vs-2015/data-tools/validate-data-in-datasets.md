---
title: Weryfikuj dane w zestawach danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d42553fbee6de6a89e16716a191db8a3d9fb883
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621070"
---
# <a name="validate-data-in-datasets"></a>Weryfikowanie danych w zestawach danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sprawdzanie poprawności danych jest procesem potwierdzającym, że wartości wprowadzane do obiektów danych są zgodne z ograniczeniami w schemacie zestawu danych. Proces weryfikacji potwierdza również, że te wartości są przestrzegane w regułach, które zostały określone dla danej aplikacji. Dobrym sposobem jest zweryfikowanie danych przed wysłaniem aktualizacji do źródłowej bazy danych. Pozwala to zmniejszyć liczbę błędów, a także potencjalne liczby operacji rundy między aplikacją a bazą danych.

 Można potwierdzić, że dane, które są zapisywane w zestawie danych, są prawidłowe przez skompilowanie kontroli walidacji do samego zestawu danych. Zestaw danych może sprawdzić dane niezależnie od sposobu wykonywania aktualizacji — bezpośrednio przez kontrolki w formularzu, w składniku lub w inny sposób. Ponieważ zestaw danych jest częścią aplikacji (w przeciwieństwie do zaplecza bazy danych), jest to miejsce logiczne do kompilowania sprawdzania poprawności specyficznej dla aplikacji.

 Najlepszym miejscem na dodanie walidacji do aplikacji jest plik klasy częściowej zestawu danych. W programie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../includes/csprcs-md.md)] Otwórz **Projektant obiektów DataSet** i kliknij dwukrotnie kolumnę lub tabelę, dla której chcesz utworzyć walidację. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> programu obsługi zdarzeń lub. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas zmiany kolumny](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) lub [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w wierszach](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Pełny przykład można znaleźć w temacie [Przewodnik: Dodawanie walidacji do zestawu danych](https://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).

## <a name="validate-data"></a>Sprawdzanie poprawności danych
 Walidację w ramach zestawu danych można wykonać w następujący sposób:

- Tworząc własne sprawdzanie poprawności specyficzne dla aplikacji, które mogą sprawdzać wartości w poszczególnych kolumnach danych podczas wprowadzania zmian.  Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w kolumnie](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- Tworząc własne sprawdzanie poprawności specyficzne dla aplikacji, które mogą sprawdzać dane do wartości podczas zmiany całego wiersza danych. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w wierszach](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

- Tworząc klucze, unikatowe ograniczenia i tak dalej, jako część rzeczywistej definicji schematu zestawu danych. Aby uzyskać więcej informacji na temat dołączania walidacji do definicji schematu, zobacz [ograniczanie kolumny danych w celu uwzględnienia unikatowych wartości](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

- Ustawiając właściwości <xref:System.Data.DataColumn> obiektu, takie jak <xref:System.Data.DataColumn.MaxLength%2A> , <xref:System.Data.DataColumn.AllowDBNull%2A> , i <xref:System.Data.DataColumn.Unique%2A> .

  <xref:System.Data.DataTable>Obiekt po wystąpieniu zmiany w rekordzie są wywoływane kilka zdarzeń:

- <xref:System.Data.DataTable.ColumnChanging>Zdarzenia i <xref:System.Data.DataTable.ColumnChanged> są wywoływane podczas każdej zmiany do pojedynczej kolumny. <xref:System.Data.DataTable.ColumnChanging>Zdarzenie jest przydatne, gdy chcesz sprawdzić poprawność zmian w określonych kolumnach. Informacje o proponowanej zmianie są przesyłane jako argument ze zdarzeniem. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w kolumnie](https://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).

- <xref:System.Data.DataTable.RowChanging>Zdarzenia i <xref:System.Data.DataTable.RowChanged> są wywoływane podczas i po każdej zmianie w wierszu. <xref:System.Data.DataTable.RowChanging>To zdarzenie jest bardziej ogólne. Wskazuje, że w wierszu występuje zmiana, ale nie wiesz, która kolumna została zmieniona. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w wierszach](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

  Domyślnie każda zmiana w kolumnie powoduje wypróbowanie czterech zdarzeń. Pierwszy to <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> zdarzenia i dla konkretnej kolumny, która jest zmieniana. Następne są <xref:System.Data.DataTable.RowChanging> zdarzenia i <xref:System.Data.DataTable.RowChanged> . W przypadku wprowadzenia wielu zmian w wierszu zdarzenia zostaną wygenerowane dla każdej zmiany.

> [!NOTE]
> Metoda wiersza danych <xref:System.Data.DataRow.BeginEdit%2A> powoduje wyłączenie <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> zdarzeń i po każdej zmianie poszczególnych kolumn. W takim przypadku zdarzenie nie jest wywoływane do momentu <xref:System.Data.DataRow.EndEdit%2A> wywołania metody, gdy <xref:System.Data.DataTable.RowChanging> <xref:System.Data.DataTable.RowChanged> zdarzenia i są wywoływane tylko raz. Aby uzyskać więcej informacji, zobacz Wyłączanie [ograniczeń podczas wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

 Wybrane zdarzenie zależy od tego, jak Szczegółowa ma być Walidacja. Jeśli ważne jest, aby przechwytywać błąd natychmiast po zmianie kolumny, walidacja kompilacji przy użyciu <xref:System.Data.DataTable.ColumnChanging> zdarzenia. W przeciwnym razie użyj <xref:System.Data.DataTable.RowChanging> zdarzenia, co może spowodować przechwycenie kilku błędów jednocześnie. Ponadto, jeśli dane są strukturalne, dzięki czemu wartość jednej kolumny jest sprawdzana na podstawie zawartości innej kolumny, a następnie przeprowadzana jest Walidacja podczas <xref:System.Data.DataTable.RowChanging> zdarzenia.

 Gdy rekordy są aktualizowane, <xref:System.Data.DataTable> obiekt zgłasza zdarzenia, na które można odpowiedzieć, ponieważ zmiany są wykonywane i po wprowadzeniu zmian.

 Jeśli aplikacja używa określonego zestawu danych, można utworzyć obsługę zdarzeń o jednoznacznie określonym typie. Spowoduje to dodanie czterech dodatkowych zdarzeń, które można utworzyć dla: `dataTableNameRowChanging` , `dataTableNameRowChanged` , `dataTableNameRowDeleting` i `dataTableNameRowDeleted` . Te typy programów obsługi zdarzeń przekazują argument, który zawiera nazwy kolumn tabeli, które ułatwiają zapisywanie i odczytywanie kodu.

## <a name="data-update-events"></a>Zdarzenia aktualizacji danych

|Wydarzenie|Opis|
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

- Opcjonalnie można użyć <xref:System.Windows.Forms.ErrorProvider> formantu, aby wyświetlić komunikat o błędzie dla użytkownika. Aby uzyskać więcej informacji, zobacz [składnik ErrorProvider](https://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).

  Walidacja może być również wykonywana podczas <xref:System.Data.DataTable.RowChanging> zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności danych podczas wprowadzania zmian w wierszach](https://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).

## <a name="validate-data-during-row-changes"></a>Sprawdzanie poprawności danych podczas zmian w wierszach
 Można napisać kod, aby sprawdzić, czy każda kolumna, która ma zostać zweryfikowana, zawiera dane, które spełniają wymagania aplikacji. W tym celu należy ustawić kolumnę, aby wskazać, że zawiera błąd, jeśli proponowana wartość jest nieakceptowalna. W poniższych przykładach określono błąd kolumny, gdy `Quantity` kolumna ma wartość 0 lub mniejszą. Procedury obsługi zdarzeń zmiany wiersza powinny wyglądać podobnie do poniższych przykładów.

#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Aby sprawdzić poprawność danych po zmianie wiersza (Visual Basic)

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [jak: otwieranie zestawu danych w Projektant obiektów DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń <xref:System.Data.DataTable> w pliku częściowej klasy zestawu danych.

    > [!TIP]
    > Kliknij dwukrotnie po lewej stronie nazwy tabeli, aby utworzyć procedurę obsługi zdarzeń zmiany wiersza. Jeśli klikniesz dwukrotnie nazwę tabeli, możesz ją edytować.

     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]

#### <a name="to-validate-data-when-a-row-changes-c"></a>Aby sprawdzić poprawność danych po zmianie wiersza (C#)

1. Otwórz zestaw danych w **Projektant obiektów DataSet**. Aby uzyskać więcej informacji, zobacz [jak: otwieranie zestawu danych w Projektant obiektów DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje utworzenie pliku częściowej klasy dla <xref:System.Data.DataTable> .

    > [!NOTE]
    > **Projektant obiektów DataSet** nie tworzy automatycznie zdarzenia obsługi dla <xref:System.Data.DataTable.RowChanging> zdarzenia. Musisz utworzyć metodę, aby obsłużyć <xref:System.Data.DataTable.RowChanging> zdarzenie, i uruchomić kod, aby podłączyć zdarzenie do metody inicjacji tabeli.

3. Skopiuj następujący kod do klasy częściowej:

    ```
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
 Każdy wiersz w tabeli danych ma <xref:System.Data.DataRow.RowState%2A> Właściwość, która śledzi bieżący stan tego wiersza przy użyciu wartości w <xref:System.Data.DataRowState> wyliczeniu. Można zwrócić zmienione wiersze z zestawu danych lub tabeli danych przez wywołanie `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> . Możesz sprawdzić, czy zmiany istnieją przed wywołaniem, `GetChanges` wywołując <xref:System.Data.DataSet.HasChanges%2A> metodę zestawu danych. Aby uzyskać więcej informacji na temat <xref:System.Data.DataSet.HasChanges%2A> , zobacz [jak: sprawdzanie zmienionych wierszy](https://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).

> [!NOTE]
> Po zatwierdzeniu zmian w zestawie danych lub tabeli danych (poprzez wywołanie <xref:System.Data.DataSet.AcceptChanges%2A> metody) `GetChanges` Metoda nie zwraca żadnych danych. Jeśli aplikacja wymaga przetworzenia zmienionych wierszy, należy przetworzyć zmiany przed wywołaniem `AcceptChanges` metody.

 Wywołanie <xref:System.Data.DataSet.GetChanges%2A> metody zestawu danych lub tabeli danych zwraca nowy zestaw danych lub tabelę danych, która zawiera tylko rekordy, które zostały zmienione. Jeśli chcesz uzyskać określone rekordy — na przykład tylko nowe rekordy lub tylko zmodyfikowane rekordy, można przekazać wartość z <xref:System.Data.DataRowState> wyliczenia jako parametr do `GetChanges` metody.

 Użyj <xref:System.Data.DataRowVersion> wyliczenia, aby uzyskać dostęp do różnych wersji wiersza (na przykład oryginalnych wartości, które znajdowały się w wierszu przed jego przetworzeniem).

#### <a name="to-get-all-changed-records-from-a-dataset"></a>Aby pobrać wszystkie zmienione rekordy z zestawu danych

- Wywoływanie <xref:System.Data.DataSet.GetChanges%2A> metody zestawu danych.

     Poniższy przykład tworzy nowy zestaw danych o nazwie `changedRecords` i wypełnia go wszystkimi zmienionymi rekordami z innego zestawu danych o nazwie `dataSet1` .

     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]

#### <a name="to-get-all-changed-records-from-a-data-table"></a>Aby pobrać wszystkie zmienione rekordy z tabeli danych

- Wywołaj <xref:System.Data.DataTable.GetChanges%2A> metodę elementu DataTable.

     Poniższy przykład tworzy nową tabelę danych o nazwie `changedRecordsTable` i wypełnia ją wszystkimi zmienionymi rekordami z innej tabeli danych o nazwie `dataTable1` .

     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]

#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Aby pobrać wszystkie rekordy z określonym stanem wiersza

- Wywołaj `GetChanges` metodę zestawu danych lub tabeli danych i przekaż <xref:System.Data.DataRowState> wartość wyliczenia jako argument.

     Poniższy przykład pokazuje, jak utworzyć nowy zestaw danych o nazwie `addedRecords` i wypełnić go tylko rekordami, które zostały dodane do `dataSet1` zestawu danych.

     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]

- Poniższy przykład pokazuje, jak zwrócić wszystkie rekordy, które zostały ostatnio dodane do `Customers` tabeli:

     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]

## <a name="access-the-original-version-of-a-datarow"></a>Dostęp do oryginalnej wersji elementu DataRow
 Gdy zmiany są wprowadzane do wierszy danych, zestaw danych zachowuje zarówno oryginalną ( <xref:System.Data.DataRowVersion> ), jak i nowe <xref:System.Data.DataRowVersion> wersje wiersza. Na przykład przed wywołaniem `AcceptChanges` metody aplikacja może uzyskać dostęp do różnych wersji rekordu (zgodnie z definicją w <xref:System.Data.DataRowVersion> wyliczeniu) i odpowiednio przetworzyć zmiany.

> [!NOTE]
> Różne wersje wiersza istnieją tylko po jego edytowaniu i przed `AcceptChanges` wywołaniem metody. Po `AcceptChanges` wywołaniu metody bieżące i oryginalne wersje są takie same.

 Przekazanie <xref:System.Data.DataRowVersion> wartości wraz z indeksem kolumny (lub nazwą kolumny jako ciągiem) zwraca wartość z określonej w wierszu wersji wiersza. Zmieniona kolumna zostanie zidentyfikowana podczas <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzeń. Jest to dobry moment, aby sprawdzić różne wersje wierszy do celów weryfikacji. Jednak jeśli ograniczenia są tymczasowo zawieszone, te zdarzenia nie zostaną wywołane i będzie trzeba programowo identyfikować kolumny, które uległy zmianie. Można to zrobić przez iterację <xref:System.Data.DataTable.Columns%2A> kolekcji i porównanie różnych <xref:System.Data.DataRowVersion> wartości.

#### <a name="to-get-the-original-version-of-a-record"></a>Aby uzyskać oryginalną wersję rekordu

- Uzyskaj dostęp do wartości kolumny, przekazując w <xref:System.Data.DataRowVersion> wierszu, który ma zostać zwrócony.

     Poniższy przykład pokazuje, jak użyć wartości, <xref:System.Data.DataRowVersion> Aby uzyskać oryginalną wartość `CompanyName` pola w <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]

## <a name="access-the-current-version-of-a-datarow"></a>Dostęp do bieżącej wersji elementu DataRow

#### <a name="to-get-the-current-version-of-a-record"></a>Aby pobrać bieżącą wersję rekordu

- Uzyskaj dostęp do wartości kolumny, a następnie Dodaj do indeksu parametr wskazujący, która wersja wiersza ma zostać zwrócona.

     Poniższy przykład pokazuje, jak użyć wartości, <xref:System.Data.DataRowVersion> Aby uzyskać bieżącą wartość `CompanyName` pola w <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]

## <a name="see-also"></a>Zobacz też

- [Instrukcje: sprawdzanie poprawności danych w kontrolce DataGridView formularzy systemu Windows](https://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)
- [Instrukcje: wyświetlanie ikon błędów dotyczących weryfikacji formularza za pomocą składnika ErrorProvider formularzy systemu Windows](https://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)