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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1e9fd28a946911a019ee0a1e144e7565bac9e004
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402722"
---
# <a name="validate-data-in-datasets"></a>Weryfikowanie danych w zestawach danych
Sprawdzanie poprawności danych jest procesem potwierdzania, że wartości wprowadzanych w obiektach danych są zgodne z ograniczeniami w schemacie elementu dataset. Proces weryfikacji potwierdza również, że postępujesz zgodnie z tych wartości reguły, które zostały utworzone dla aplikacji. Jest dobrą praktyką, aby sprawdzić poprawność danych przed wysłaniem aktualizacji do podstawowej bazy danych. Zmniejsza to błędy, a także potencjalną liczbę rund między aplikacją a bazą danych.

Możesz potwierdzić, że dane, które są zapisywane do zestawu danych jest prawidłowy, tworząc sprawdzanie poprawności do zestawu danych. Zestaw danych można sprawdzić dane, niezależnie od tego, jak jest wykonywana aktualizacja — czy bezpośrednio przez kontrolek w formularzu w składniku lub w inny sposób. Ponieważ zestaw danych jest częścią Twojej aplikacji (w przeciwieństwie do bazy danych zaplecza), jest logiczne miejsce do kompilacji sprawdzania poprawności specyficznych dla aplikacji.

Jest najlepszym miejscem, aby dodać sprawdzanie poprawności do aplikacji w pliku częściowej klasy zestawu danych. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], otwórz **Projektanta obiektów Dataset** i dwukrotnie kliknij kolumny lub tabeli, dla której chcesz utworzyć sprawdzania poprawności. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> programu obsługi zdarzeń.

## <a name="validate-data"></a>Sprawdzanie poprawności danych
 Sprawdzanie poprawności w zestawie danych odbywa się w następujący sposób:

- Tworząc własne weryfikacji specyficzne dla aplikacji, które sprawdza, czy wartości w kolumnie danych podczas zmiany. Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas zmiany kolumn](validate-data-in-datasets.md).

- Tworząc własne weryfikacji specyficzne dla aplikacji, które sprawdza, czy dane wartości podczas całego danymi wiersza ulegnie zmianie. Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach](validate-data-in-datasets.md).

- Tworząc klucze, ograniczenia unikatowe, i tak dalej jako część definicji rzeczywiste schemat zestawu danych.

- Przez ustawienie właściwości <xref:System.Data.DataColumn> obiektu, takie jak <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, i <xref:System.Data.DataColumn.Unique%2A>.

Kilka zdarzeń są inicjowane przez <xref:System.Data.DataTable> obiektu, kiedy zmiana odbywa się w rekordzie:

- <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia są wywoływane podczas i po każdej zmianie do poszczególnych kolumn. <xref:System.Data.DataTable.ColumnChanging> Zdarzeń jest przydatne w przypadku, gdy chcesz zweryfikować zmiany w określonych kolumnach. Informacje o proponowana zmiana jest przekazywany jako argument ze zdarzeniem.
- <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia są wywoływane podczas i po każdym zmianę w wierszu. <xref:System.Data.DataTable.RowChanging> Zdarzeń jest bardziej ogólny. Oznacza, że zmiany występuje gdzieś w wierszu, ale nie wiesz, która kolumna została zmieniona.

Domyślnie każda zmiana z kolumną w związku z tym wywołuje cztery zdarzenia. Pierwsza to <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia dla określonej kolumny, która jest zmieniany. Następnie są <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia. Jeśli wiersz wprowadzono wiele zmian, zdarzenia zostanie wygenerowany dla każdej zmiany.

> [!NOTE]
> Wiersz danych <xref:System.Data.DataRow.BeginEdit%2A> metoda wyłącza <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia po każdej zmianie poszczególnych kolumn. W takim przypadku zdarzenie nie zostanie wywołane do momentu <xref:System.Data.DataRow.EndEdit%2A> metoda została wywołana, gdy <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia są wywoływane tylko raz. Aby uzyskać więcej informacji, zobacz [wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Zdarzenia, które wybierzesz, zależy od tego, szczegółowość sprawdzenie poprawności jako. Jeśli jest to ważne, wychwycić błąd, natychmiast podczas zmiany kolumny, Tworzenie weryfikacji za pomocą <xref:System.Data.DataTable.ColumnChanging> zdarzeń. W przeciwnym razie użyj <xref:System.Data.DataTable.RowChanging> zdarzenie, które może prowadzić do przechwytywania kilka błędów od razu. Ponadto, jeśli dane mają strukturę, aby wartość jednej kolumny jest weryfikowana, na podstawie zawartości innej kolumny, Przeprowadź walidację podczas <xref:System.Data.DataTable.RowChanging> zdarzeń.

Po zaktualizowaniu rekordów <xref:System.Data.DataTable> obiektu wywołuje zdarzenia, które można odpowiedzieć występują zmiany i po dokonaniu zmian.

Jeśli aplikacja używa typizowany zestaw danych, można utworzyć procedury obsługi zdarzeń silnie typizowanych. Spowoduje to dodanie cztery dodatkowe zdarzenia kontrolą typów, dla których można utworzyć procedury obsługi: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, i `dataTableNameRowDeleted`. Te procedury obsługi zdarzeń wpisane przekazać argument, który zawiera nazwy kolumn tabeli, które ułatwiają kodu do zapisu i odczytu.

## <a name="data-update-events"></a>Dane zdarzeń aktualizacji

|Zdarzenie|Opis|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Wartość w kolumnie jest zmieniany. Zdarzenie przekazuje wiersza i kolumny, wraz z proponowaną nową wartość.|
|<xref:System.Data.DataTable.ColumnChanged>|Wartość w kolumnie została zmieniona. Zdarzenie przekazuje wiersza i kolumny, wraz z proponowana wartość.|
|<xref:System.Data.DataTable.RowChanging>|Zmiany wprowadzone do <xref:System.Data.DataRow> obiektu mają być przekazane do zestawu danych. Jeśli nie wywołano <xref:System.Data.DataRow.BeginEdit%2A> metody <xref:System.Data.DataTable.RowChanging> zdarzenie jest wywoływane dla każdej zmiany z kolumną natychmiast po <xref:System.Data.DataTable.ColumnChanging> spowodował zdarzenie. Jeśli wywołujesz <xref:System.Data.DataRow.BeginEdit%2A> przed wprowadzeniem zmian, <xref:System.Data.DataTable.RowChanging> zdarzenie jest zgłaszane tylko wtedy, gdy wywołujesz <xref:System.Data.DataRow.EndEdit%2A> metody.<br /><br /> Zdarzenie przekazuje wiersza, oraz wartość wskazującą, jakiego typu akcji (zmiana, wstawiania i tak dalej) jest wykonywana.|
|<xref:System.Data.DataTable.RowChanged>|Wiersz został zmieniony. Zdarzenie przekazuje wiersza, oraz wartość wskazującą, jakiego typu akcji (zmiana, wstawiania i tak dalej) jest wykonywana.|
|<xref:System.Data.DataTable.RowDeleting>|Wiersz jest usuwana. Zdarzenie przekazuje wiersza, oraz wartość wskazującą, jakiego typu akcji (Usuń) jest wykonywana.|
|<xref:System.Data.DataTable.RowDeleted>|Wiersz został usunięty. Zdarzenie przekazuje wiersza, oraz wartość wskazującą, jakiego typu akcji (Usuń) jest wykonywana.|

<xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, I <xref:System.Data.DataTable.RowDeleting> zdarzenia są wywoływane podczas procesu aktualizacji. Sprawdzanie poprawności danych lub wykonywać inne typy przetwarzania, można użyć tych zdarzeń. Ponieważ ta aktualizacja jest w toku podczas tych zdarzeń, możesz to anulować, zostanie zgłoszony wyjątek, który uniemożliwia aktualizację z zakończeniem.

<xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> i <xref:System.Data.DataTable.RowDeleted> zdarzenia to zdarzenia powiadomień, które są wywoływane, gdy aktualizacja została zakończona pomyślnie. Zdarzenia te są przydatne do podjęcia dalszych czynności w oparciu o pomyślnej aktualizacji.

## <a name="validate-data-during-column-changes"></a>Sprawdzanie poprawności danych podczas zmiany kolumn

> [!NOTE]
> **Projektanta obiektów Dataset** tworzy częściową klas, które weryfikacji logiki może być dodana do zestawu danych. Zestaw wygenerowany przez projektanta danych nie usuniesz lub zmienisz każdy kod w klasie częściowej.

Można sprawdzić poprawność danych po zmianie wartości w kolumnie danych odpowiedzi na <xref:System.Data.DataTable.ColumnChanging> zdarzeń. Gdy wywoływane, zdarzenie to przekazuje argument zdarzeń (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) zawierający wartość, która jest proponowany dla bieżącej kolumny. Oparte na zawartości `e.ProposedValue`, możesz:

- Zaakceptuj wartość proponowaną przez czynności.

- Odrzuć proponowaną wartość przez ustawienie błędu kolumny (<xref:System.Data.DataRow.SetColumnError%2A>) z w ramach programu obsługi zdarzeń zmiany kolumny.

- Opcjonalnie użyć <xref:System.Windows.Forms.ErrorProvider> formantu, aby wyświetlić komunikat o błędzie dla użytkownika. Aby uzyskać więcej informacji, zobacz [ErrorProvider, składnik](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Można również wykonać sprawdzanie poprawności podczas <xref:System.Data.DataTable.RowChanging> zdarzeń.

## <a name="validate-data-during-row-changes"></a>Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach
Można napisać kod, aby sprawdzić, czy każda kolumny, której chcesz sprawdzić zawiera dane, które spełniają wymagania aplikacji. To zrobić, ustawiając kolumny, aby wskazać, że zawiera błąd, jeżeli proponowana wartość jest nieakceptowana. W następujących przykładach ustawiona jest błąd kolumny gdy `Quantity` kolumna jest mniejsza lub równa 0. Programy obsługi zdarzeń zmiany wiersza powinien przypominać poniższe przykłady.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Do sprawdzania poprawności danych, gdy wiersz zmieni (Visual Basic)

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.RowChanging> program obsługi zdarzeń <xref:System.Data.DataTable> w pliku częściowej klasy zestawu danych.

    > [!TIP]
    > Kliknij dwukrotnie po lewej stronie nazwy tabeli, aby utworzyć procedury obsługi zdarzeń zmiany wiersza. Jeśli klikniesz dwukrotnie nazwę tabeli, można go edytować.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Aby sprawdzić poprawność danych, gdy wiersz zmieni (C#)

1. Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja tworzy plik częściowy klasy dla <xref:System.Data.DataTable>.

    > [!NOTE]
    > **Projektanta obiektów Dataset** nie tworzy automatycznie zdarzenia obsługi dla <xref:System.Data.DataTable.RowChanging> zdarzeń. Należy utworzyć metody, aby obsłużyć <xref:System.Data.DataTable.RowChanging> zdarzeń i wykonywania kodu, aby zaczepić zdarzenie w metodzie inicjalizacji tabeli.

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

## <a name="to-retrieve-changed-rows"></a>Pobieranie zmienionych wierszy
Każdy wiersz w tabeli danych ma <xref:System.Data.DataRow.RowState%2A> właściwość, która przechowuje informacje o bieżący stan tego wiersza przy użyciu wartości w <xref:System.Data.DataRowState> wyliczenia. Może zwrócić zmienionych wierszy z tabeli zestawu danych lub dane, wywołując `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>. Możesz sprawdzić, czy istnieją zmiany przed wywołaniem `GetChanges` przez wywołanie metody <xref:System.Data.DataSet.HasChanges%2A> metoda zestawu danych.

> [!NOTE]
> Po zatwierdzeniu zmiany do zestawu danych lub danych tabeli (przez wywołanie metody <xref:System.Data.DataSet.AcceptChanges%2A> metoda), `GetChanges` metoda nie zwraca żadnych danych. Jeśli Twoja aplikacja potrzebuje do przetwarzania zmienionych wierszy, musisz przetwarzać zmiany przed wywołaniem `AcceptChanges` metody.

Wywoływanie <xref:System.Data.DataSet.GetChanges%2A> metoda zestawu danych lub danych tabeli zwraca nową tabelę zestawu danych lub danych, która zawiera tylko rekordy, które zostały zmienione. Jeśli chcesz uzyskać konkretne rekordy — na przykład tylko nowe rekordy lub tylko zmodyfikowanych rekordów — można przekazać wartość z zakresu od <xref:System.Data.DataRowState> wyliczenia jako parametr do `GetChanges` metody.

Użyj <xref:System.Data.DataRowVersion> wyliczeniu, aby uzyskać dostęp do różnych wersji wierszy (na przykład, oryginalne wartości, które były w wierszu przed jego przetworzeniem).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Aby uzyskać wszystkie zmienionych rekordów z zestawu danych

- Wywołaj <xref:System.Data.DataSet.GetChanges%2A> metoda zestawu danych.

     Poniższy przykład tworzy nowy zestaw danych o nazwie `changedRecords` i wypełnia zmienionych rekordów z innego zestawu danych o nazwie `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Aby uzyskać wszystkie zmienionych rekordów z tabeli danych

- Wywołaj <xref:System.Data.DataTable.GetChanges%2A> metoda DataTable.

     Poniższy przykład tworzy nową tabelę danych o nazwie `changedRecordsTable` i wypełnia zmienionych rekordów z innej tabeli danych o nazwie `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Aby uzyskać wszystkie rekordy, które mają stan konkretnego wiersza

- Wywołaj `GetChanges` metoda zestawu danych lub tabela danych i przekazać <xref:System.Data.DataRowState> wartość wyliczenia jako argument.

     Poniższy przykład pokazuje, jak utworzyć nowy zestaw danych o nazwie `addedRecords` i wypełnić je tylko w przypadku rekordów, które zostały dodane do `dataSet1` zestawu danych.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Poniższy przykład pokazuje, jak i zwracać wszystkie rekordy, które zostały ostatnio dodane do `Customers` tabeli:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Dostęp do oryginalnej wersji DataRow
Gdy zostaną wprowadzone zmiany do wierszy danych, zestaw danych zachowuje zarówno oryginał (<xref:System.Data.DataRowVersion.Original>) i nowe (<xref:System.Data.DataRowVersion.Current>) wersje wiersza. Na przykład przed wywołaniem `AcceptChanges` metody, Twoja aplikacja ma dostęp do różnych wersji rekordu (zgodnie z definicją w <xref:System.Data.DataRowVersion> wyliczenie) i odpowiednio przetworzyć zmiany.

> [!NOTE]
> Istnieją różne wersje wiersza, tylko wtedy, gdy był edytowany i przed `AcceptChanges` została wywołana metoda. Po `AcceptChanges` wywołano metodę, bieżąca i oryginalna wersja są takie same.

Przekazywanie <xref:System.Data.DataRowVersion> wartości wraz z indeks kolumny (lub nazwy kolumny jako ciąg) zwraca wartość z tej kolumny określonego wiersza wersji. Zmieniona kolumna jest określana w trakcie <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia. Jest to dobry moment, aby sprawdzić wersje innego wiersza do celów sprawdzania poprawności. Jednak jeśli ograniczenia zostały tymczasowo zawieszone, te zdarzenia nie będą wywoływane i trzeba będzie programowo zidentyfikować, kolumny, które zostały zmienione. Można to zrobić przez iterację <xref:System.Data.DataTable.Columns%2A> zbieranie i porównywanie różnych <xref:System.Data.DataRowVersion> wartości.

### <a name="to-get-the-original-version-of-a-record"></a>Aby uzyskać oryginalną wersję rekordu

- Dostęp do wartości kolumny, przekazując <xref:System.Data.DataRowVersion> wiersza mają być zwracane.

     Poniższy przykład pokazuje, jak używać <xref:System.Data.DataRowVersion> wartości, aby uzyskać oryginalnej wartości elementu `CompanyName` pole <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Dostęp do bieżącej wersji DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Aby uzyskać bieżącą wersję rekordu

- Dostęp do wartości kolumny, a następnie dodaj parametr do indeksu, który wskazuje na to, którą wersję wiersza należy zwrócić.

     Poniższy przykład pokazuje, jak używać <xref:System.Data.DataRowVersion> wartości, aby uzyskać bieżącą wartość `CompanyName` pole <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Instrukcje: Sprawdzanie poprawności danych w formancie DataGridView formularzy Windows](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Instrukcje: Wyświetlanie ikon błędów dla walidacji formularza za pomocą składnika ErrorProvider formularzy Windows](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)