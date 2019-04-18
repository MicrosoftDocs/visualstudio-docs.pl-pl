---
title: Sprawdzanie poprawności danych w zestawach danych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 73eb1162411800a951566c9eb14928875966cfb7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661324"
---
# <a name="validate-data-in-datasets"></a>Weryfikowanie danych w zestawach danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sprawdzanie poprawności danych jest procesem potwierdzania, że wartości wprowadzanych w obiektach danych są zgodne z ograniczeniami w schemacie elementu dataset. Proces weryfikacji potwierdza również, że postępujesz zgodnie z tych wartości reguły, które zostały utworzone dla aplikacji. Jest dobrą praktyką, aby sprawdzić poprawność danych przed wysłaniem aktualizacji do podstawowej bazy danych. Zmniejsza to błędy, a także potencjalną liczbę rund między aplikacją a bazą danych.  
  
 Możesz potwierdzić, że dane, które są zapisywane do zestawu danych jest prawidłowy, tworząc sprawdzanie poprawności do zestawu danych. Zestaw danych można sprawdzić dane, niezależnie od tego, jak jest wykonywana aktualizacja — czy bezpośrednio przez kontrolek w formularzu w składniku lub w inny sposób. Ponieważ zestaw danych jest częścią Twojej aplikacji (w przeciwieństwie do bazy danych zaplecza), jest logiczne miejsce do kompilacji sprawdzania poprawności specyficznych dla aplikacji.  
  
 Jest najlepszym miejscem, aby dodać sprawdzanie poprawności do aplikacji w pliku częściowej klasy zestawu danych. W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../includes/csprcs-md.md)], otwórz **Projektanta obiektów Dataset** i dwukrotnie kliknij kolumny lub tabeli, dla której chcesz utworzyć sprawdzania poprawności. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> programu obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas zmiany kolumn](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) lub [jak: Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Aby uzyskać kompletny przykład, zobacz [instruktażu: Dodawanie walidacji do zestawu danych](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
## <a name="validate-data"></a>Sprawdzanie poprawności danych  
 Sprawdzanie poprawności w zestawie danych może się odbywać w następujący sposób:  
  
- Tworząc własne weryfikacji specyficzne dla aplikacji, które sprawdza, czy wartości w kolumnie danych podczas zmiany.  Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas zmiany kolumn](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- Tworząc własne weryfikacji specyficzne dla aplikacji, które sprawdza, czy dane wartości podczas całego danymi wiersza ulegnie zmianie. Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
- Tworząc klucze, ograniczenia unikatowe, i tak dalej jako część definicji rzeczywiste schemat zestawu danych. Aby uzyskać więcej informacji o dołączaniu sprawdzania poprawności do definicji schematu, zobacz [ograniczając DataColumn zawiera unikatowe wartości](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
- Przez ustawienie właściwości <xref:System.Data.DataColumn> obiektu, takie jak <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, i <xref:System.Data.DataColumn.Unique%2A>.  
  
  Kilka zdarzeń są inicjowane przez <xref:System.Data.DataTable> obiektu, kiedy zmiana odbywa się w rekordzie:  
  
- <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia są wywoływane podczas i po każdej zmianie do poszczególnych kolumn. <xref:System.Data.DataTable.ColumnChanging> Zdarzeń jest przydatne w przypadku, gdy chcesz zweryfikować zmiany w określonych kolumnach. Informacje o proponowana zmiana jest przekazywany jako argument ze zdarzeniem. Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas zmiany kolumn](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia są wywoływane podczas i po każdym zmianę w wierszu. <xref:System.Data.DataTable.RowChanging> Zdarzeń jest bardziej ogólny. Oznacza, że zmiany występuje gdzieś w wierszu, ale nie wiesz, która kolumna została zmieniona. Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
  Domyślnie każda zmiana z kolumną w związku z tym wywołuje cztery zdarzenia. Pierwsza to <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia dla określonej kolumny, która jest zmieniany. Następnie są <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia. Jeśli wiersz wprowadzono wiele zmian, zdarzenia zostanie wygenerowany dla każdej zmiany.  
  
> [!NOTE]
>  Wiersz danych <xref:System.Data.DataRow.BeginEdit%2A> metoda wyłącza <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia po każdej zmianie poszczególnych kolumn. W takim przypadku zdarzenie nie zostanie wywołane do momentu <xref:System.Data.DataRow.EndEdit%2A> metoda została wywołana, gdy <xref:System.Data.DataTable.RowChanging> i <xref:System.Data.DataTable.RowChanged> zdarzenia są wywoływane tylko raz. Aby uzyskać więcej informacji, zobacz [wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 Zdarzenia, które wybierzesz, zależy od tego, szczegółowość sprawdzenie poprawności jako. Jeśli jest to ważne, wychwycić błąd, natychmiast podczas zmiany kolumny, Tworzenie weryfikacji za pomocą <xref:System.Data.DataTable.ColumnChanging> zdarzeń. W przeciwnym razie użyj <xref:System.Data.DataTable.RowChanging> zdarzenie, które może prowadzić do przechwytywania kilka błędów od razu. Ponadto, jeśli dane mają strukturę, aby wartość jednej kolumny jest weryfikowana, na podstawie zawartości innej kolumny, następnie Przeprowadź walidację podczas <xref:System.Data.DataTable.RowChanging> zdarzeń.  
  
 Po zaktualizowaniu rekordów <xref:System.Data.DataTable> obiektu wywołuje zdarzenia, które można odpowiedzieć występują zmiany i po dokonaniu zmian.  
  
 Jeśli aplikacja używa typizowany zestaw danych, można utworzyć procedury obsługi zdarzeń silnie typizowanych. Spowoduje to dodanie cztery dodatkowe zdarzenia kontrolą typów, które można utworzyć procedury obsługi dla: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, i `dataTableNameRowDeleted`. Te procedury obsługi zdarzeń wpisane przekazać argument, który zawiera nazwy kolumn tabeli, które ułatwiają kodu do zapisu i odczytu.  
  
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
>  **Projektanta obiektów Dataset** tworzy częściową klas, które weryfikacji logiki może być dodana do zestawu danych. Zestaw wygenerowany przez projektanta danych nie usuniesz lub zmienisz każdy kod w klasie częściowej.  
  
 Można sprawdzić poprawność danych po zmianie wartości w kolumnie danych odpowiedzi na <xref:System.Data.DataTable.ColumnChanging> zdarzeń. Gdy wywoływane, zdarzenie to przekazuje argument zdarzeń (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>) zawierający wartość, która jest proponowany dla bieżącej kolumny. Oparte na zawartości `e.ProposedValue`, możesz:  
  
- Zaakceptuj wartość proponowaną przez czynności.  
  
- Odrzuć proponowaną wartość przez ustawienie błędu kolumny (<xref:System.Data.DataRow.SetColumnError%2A>) z w ramach programu obsługi zdarzeń zmiany kolumny.  
  
- Opcjonalnie użyć <xref:System.Windows.Forms.ErrorProvider> formantu, aby wyświetlić komunikat o błędzie dla użytkownika. Aby uzyskać więcej informacji, zobacz [ErrorProvider, składnik](http://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).  
  
  Można również wykonać sprawdzanie poprawności podczas <xref:System.Data.DataTable.RowChanging> zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
## <a name="validate-data-during-row-changes"></a>Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach  
 Można napisać kod, aby sprawdzić, czy każda kolumny, której chcesz sprawdzić zawiera dane, które spełniają wymagania aplikacji. To zrobić, ustawiając kolumny, aby wskazać, że zawiera błąd, jeżeli proponowana wartość jest nieakceptowana. W następujących przykładach ustawiona jest błąd kolumny gdy `Quantity` kolumna jest mniejsza lub równa 0. Programy obsługi zdarzeń zmiany wiersza powinien przypominać poniższe przykłady.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Do sprawdzania poprawności danych, gdy wiersz zmieni (Visual Basic)  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [jak: Otwórz zestaw danych w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja powoduje automatyczne utworzenie <xref:System.Data.DataTable.RowChanging> program obsługi zdarzeń <xref:System.Data.DataTable> w pliku częściowej klasy zestawu danych.  
  
    > [!TIP]
    >  Kliknij dwukrotnie po lewej stronie nazwy tabeli, aby utworzyć procedury obsługi zdarzeń zmiany wiersza. Jeśli klikniesz dwukrotnie nazwę tabeli, można go edytować.  
  
     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Aby sprawdzić poprawność danych, gdy wiersz zmieni (C#)  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [jak: Otwórz zestaw danych w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Kliknij dwukrotnie pasek tytułu tabeli, którą chcesz zweryfikować. Ta akcja tworzy plik częściowy klasy dla <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    >  **Projektanta obiektów Dataset** nie tworzy automatycznie zdarzenia obsługi dla <xref:System.Data.DataTable.RowChanging> zdarzeń. Należy utworzyć metody, aby obsłużyć <xref:System.Data.DataTable.RowChanging> zdarzeń i wykonywania kodu, aby zaczepić zdarzenie w metodzie inicjalizacji tabeli.  
  
3.  Skopiuj następujący kod do klasy częściowej:  
  
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
  
## <a name="to-retrieve-changed-rows"></a>Pobieranie zmienionych wierszy  
 Każdy wiersz w tabeli danych ma <xref:System.Data.DataRow.RowState%2A> właściwość, która przechowuje informacje o bieżący stan tego wiersza przy użyciu wartości w <xref:System.Data.DataRowState> wyliczenia. Może zwrócić zmienionych wierszy z tabeli zestawu danych lub dane, wywołując `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>. Możesz sprawdzić, czy istnieją zmiany przed wywołaniem `GetChanges` przez wywołanie metody <xref:System.Data.DataSet.HasChanges%2A> metoda zestawu danych. Aby uzyskać więcej informacji na temat <xref:System.Data.DataSet.HasChanges%2A>, zobacz [jak: Wyszukiwanie zmienionych wierszy](http://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).  
  
> [!NOTE]
>  Po zatwierdzeniu zmiany do zestawu danych lub danych tabeli (przez wywołanie metody <xref:System.Data.DataSet.AcceptChanges%2A> metoda), `GetChanges` metoda nie zwraca żadnych danych. Jeśli Twoja aplikacja potrzebuje do przetwarzania zmienionych wierszy, musisz przetwarzać zmiany przed wywołaniem `AcceptChanges` metody.  
  
 Wywoływanie <xref:System.Data.DataSet.GetChanges%2A> metoda zestawu danych lub danych tabeli zwraca nową tabelę zestawu danych lub danych, która zawiera tylko rekordy, które zostały zmienione. Jeśli chcesz uzyskać konkretne rekordy — na przykład tylko nowe rekordy lub tylko zmodyfikowanych rekordów — można przekazać wartość z zakresu od <xref:System.Data.DataRowState> wyliczenia jako parametr do `GetChanges` metody.  
  
 Użyj <xref:System.Data.DataRowVersion> wyliczeniu, aby uzyskać dostęp do różnych wersji wierszy (na przykład, oryginalne wartości, które były w wierszu przed jego przetworzeniem).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Aby uzyskać wszystkie zmienionych rekordów z zestawu danych  
  
-   Wywołaj <xref:System.Data.DataSet.GetChanges%2A> metoda zestawu danych.  
  
     Poniższy przykład tworzy nowy zestaw danych o nazwie `changedRecords` i wypełnia zmienionych rekordów z innego zestawu danych o nazwie `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Aby uzyskać wszystkie zmienionych rekordów z tabeli danych  
  
-   Wywołaj <xref:System.Data.DataTable.GetChanges%2A> metoda DataTable.  
  
     Poniższy przykład tworzy nową tabelę danych o nazwie `changedRecordsTable` i wypełnia zmienionych rekordów z innej tabeli danych o nazwie `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Aby uzyskać wszystkie rekordy, które mają stan konkretnego wiersza  
  
-   Wywołaj `GetChanges` metoda zestawu danych lub tabela danych i przekazać <xref:System.Data.DataRowState> wartość wyliczenia jako argument.  
  
     Poniższy przykład pokazuje, jak utworzyć nowy zestaw danych o nazwie `addedRecords` i wypełnić je tylko w przypadku rekordów, które zostały dodane do `dataSet1` zestawu danych.  
  
     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]  
  
-   Poniższy przykład pokazuje, jak i zwracać wszystkie rekordy, które zostały ostatnio dodane do `Customers` tabeli:  
  
     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Dostęp do oryginalnej wersji DataRow  
 Gdy zostaną wprowadzone zmiany do wierszy danych, zestaw danych zachowuje zarówno oryginał (<xref:System.Data.DataRowVersion>) i nowe (<xref:System.Data.DataRowVersion>) wersje wiersza. Na przykład przed wywołaniem `AcceptChanges` metody, Twoja aplikacja ma dostęp do różnych wersji rekordu (zgodnie z definicją w <xref:System.Data.DataRowVersion> wyliczenie) i odpowiednio przetworzyć zmiany.  
  
> [!NOTE]
>  Istnieją różne wersje wiersza, tylko wtedy, gdy był edytowany i przed `AcceptChanges` została wywołana metoda. Po `AcceptChanges` wywołano metodę, bieżąca i oryginalna wersja są takie same.  
  
 Przekazywanie <xref:System.Data.DataRowVersion> wartości wraz z indeks kolumny (lub nazwy kolumny jako ciąg) zwraca wartość z tej kolumny określonego wiersza wersji. Zmieniona kolumna jest określana w trakcie <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.ColumnChanged> zdarzenia. Jest to dobry moment, aby sprawdzić wersje innego wiersza do celów sprawdzania poprawności. Jednak jeśli ograniczenia zostały tymczasowo zawieszone, te zdarzenia nie będą wywoływane i trzeba będzie programowo zidentyfikować, kolumny, które zostały zmienione. Można to zrobić przez iterację <xref:System.Data.DataTable.Columns%2A> zbieranie i porównywanie różnych <xref:System.Data.DataRowVersion> wartości.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Aby uzyskać oryginalną wersję rekordu  
  
-   Dostęp do wartości kolumny, przekazując <xref:System.Data.DataRowVersion> wiersza mają być zwracane.  
  
     Poniższy przykład pokazuje, jak używać <xref:System.Data.DataRowVersion> wartości, aby uzyskać oryginalnej wartości elementu `CompanyName` pole <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Dostęp do bieżącej wersji DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Aby uzyskać bieżącą wersję rekordu  
  
-   Dostęp do wartości kolumny, a następnie dodaj parametr do indeksu, który wskazuje na to, którą wersję wiersza należy zwrócić.  
  
     Poniższy przykład pokazuje, jak używać <xref:System.Data.DataRowVersion> wartości, aby uzyskać bieżącą wartość `CompanyName` pole <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](http://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)   
- [Instrukcje: Wyświetlanie ikon błędów weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows](http://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)