---
title: Zapisywanie danych z powrotem w bazie danych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b3bbb8b93eb4b2f0cc1078224118b41caa590df6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966962"
---
# <a name="save-data-back-to-the-database"></a>Zapisywanie danych z powrotem w bazie danych

Zestaw danych jest kopii danych w pamięci. W przypadku zmodyfikowania tych danych jest dobrą praktyką, aby zapisać te zmiany w bazie danych. Możesz to zrobić na jeden z trzech sposobów:

- Przez wywołanie jednej z `Update` metod TableAdapter

- Przez wywołanie jednej z `DBDirect` metod TableAdapter

- Przez wywołanie metody `UpdateAll` metody TableAdapterManager, że program Visual Studio generuje dla Ciebie, gdy zestaw danych zawiera tabele, które są powiązane z innymi tabelami w zestawie danych

Wiążąc danych tabel w zestawie danych z kontrolkami w formularzu Windows lub XAML na stronie, architektura powiązanie danych wykonuje całą pracę za Ciebie.

Jeśli znasz TableAdapters, możesz przejść bezpośrednio do jednego z tych tematów:

|Temat|Opis|
|-----------|-----------------|
|[Wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md)|Jak przeprowadzić aktualizacje i wstawia przy użyciu obiektów TableAdapter lub polecenia|
|[Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Jak przeprowadzić aktualizacje z TableAdapters|
|[Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)|Jak przeprowadzić aktualizacje z zestawu danych przy użyciu dwóch lub więcej powiązanych tabel|
|[Obsługiwanie wyjątku współbieżności](../data-tools/handle-a-concurrency-exception.md)|Jak obsługiwać wyjątki, gdy dwóch użytkowników podejmują próby zmiany te same dane w bazie danych, w tym samym czasie|
|[Instrukcje: Zapisywanie danych przy użyciu transakcji](../data-tools/save-data-by-using-a-transaction.md)|Jak zapisać danych w ramach transakcji przy użyciu systemu. Transactions — przestrzeń nazw i obiekt elementu TransactionScope|
|[Zapisywanie danych w transakcji](../data-tools/save-data-in-a-transaction.md)|Przewodnik, który pokazuje tworzenie aplikacji Windows Forms, aby zademonstrować zapisywanie danych do bazy danych w obrębie transakcji|
|[Zapisywanie danych w bazie danych (wiele tabel)](../data-tools/save-data-to-a-database-multiple-tables.md)|Jak edytować rekordy i zapisać zmiany w wielu tabel w bazie danych|
|[Zapisywanie danych z obiektu w bazie danych](../data-tools/save-data-from-an-object-to-a-database.md)|Sposób przekazywania danych z obiektu, który nie jest w zestawie danych do bazy danych za pomocą TableAdapter dbdirect — metody|
|[Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Jak wysyłać zapytania SQL bezpośrednio do bazy danych za pomocą TableAdapter|
|[Zapisywanie zestawu danych jako kodu XML](../data-tools/save-a-dataset-as-xml.md)|Jak zapisać zestawu danych do dokumentu XML|

## <a name="two-stage-updates"></a>Aktualizacje dwuetapowego

Aktualizowanie źródła danych jest procesem dwuetapowym. Pierwszym krokiem jest aktualizacji zestawu danych za pomocą nowych rekordów, zmienionych rekordów lub usuniętych rekordów. Jeśli Twoja aplikacja nigdy nie przesyła te zmiany do źródła danych, jesteś gotowy wraz z aktualizacją.

Jeśli wyślesz zmiany w bazie danych, drugi krok jest wymagany. Jeśli nie używasz kontrolek powiązanych z danymi, musisz ręcznie wywołać `Update` metoda ten sam obiekt TableAdapter (lub adapter danych), używany do wypełniania zestawu danych. Jednak umożliwia także różne karty, na przykład, aby przenieść dane z jednego źródła danych do innego lub zaktualizować wiele źródeł danych. Jeśli nie są używane powiązanie danych i zapisywania zmian dla tabel powiązanych, należy ręcznie utworzyć wystąpienie zmiennej generowanych automatycznie `TableAdapterManager` klasy, a następnie wywołać jej `UpdateAll` metody.

![Diagram pojęciowy aktualizacje zbiorów danych](../data-tools/media/vbdatasetupdates.gif)

Zestaw danych zawiera kolekcje tabel, które zawierają kolekcji wierszy. Jeśli zamierzasz później zaktualizować źródła danych, należy użyć metody na `DataTable.DataRowCollection` właściwości podczas dodawania lub usuwania wierszy. Te metody wykonywania śledzenia zmian, potrzebne do aktualizowania źródła danych. Jeśli wywołasz `RemoveAt` kolekcji właściwości wierszy, usunięcie nie będą przekazywane w bazie danych.

## <a name="merge-datasets"></a>Scalanie zestawów danych

Można zaktualizować zawartości zestawu danych przez *scalanie* go z innym zestawem danych. Operacja obejmuje skopiowanie zawartość *źródła* zestawu danych do wywoływania zestawu danych (nazywane *docelowej* zestawu danych). Przy scalaniu zestawów danych, nowych rekordów w zestawie danych źródłowych są dodawane do zestawu danych docelowego. Ponadto dodatkowe kolumny w zestawie danych źródłowych są dodawane do zestawu danych docelowego. Scalanie zestawów danych jest przydatne w przypadku, gdy zestaw danych lokalnych, a uzyskasz drugi zestaw danych z innej aplikacji. Jest również przydatne, gdy otrzymasz drugi zestaw danych od składnika, takiego jak usługi sieci web XML lub gdy potrzebujesz integrować dane z wielu zestawów danych.

Podczas scalania zestawów danych, można przekazać argument logiczny (`preserveChanges`) informuje, że <xref:System.Data.DataSet.Merge%2A> metoda czy zachować istniejące zmiany w zestawie danych docelowych. Ponieważ zestawy danych, obsługa wielu wersji rekordy, należy pamiętać o więcej niż jedna wersja rekordów jest scalana. W poniższej tabeli przedstawiono, jak został scalony rekord w dwóch zestawów danych:

|DataRowVersion|Docelowy dataset|Zestaw danych źródłowych|
| - | - | - |
|Oryginał|James Wilson|James C. Wilson|
|bieżący|Jim Wilson|James C. Wilson|

Wywoływanie <xref:System.Data.DataSet.Merge%2A> metody w poprzedniej tabeli za pomocą `preserveChanges=false targetDataset.Merge(sourceDataset)` powoduje następujące dane:

|DataRowVersion|Docelowy dataset|Zestaw danych źródłowych|
| - | - | - |
|Oryginał|James C. Wilson|James C. Wilson|
|bieżący|James C. Wilson|James C. Wilson|

Wywoływanie <xref:System.Data.DataSet.Merge%2A> metody z `preserveChanges = true targetDataset.Merge(sourceDataset, true)` powoduje następujące dane:

|DataRowVersion|Docelowy dataset|Zestaw danych źródłowych|
| - | - | - |
|Oryginał|James C. Wilson|James C. Wilson|
|bieżący|Jim Wilson|James C. Wilson|

> [!CAUTION]
> W `preserveChanges = true` scenariusz, jeśli <xref:System.Data.DataSet.RejectChanges%2A> metoda jest wywoływana w rekordu w zestawie danych docelowych, a następnie przywraca pierwotne dane z *źródła* zestawu danych. Oznacza to, że próbujesz zaktualizować oryginalnego źródła danych przy użyciu docelowy dataset nie prawdopodobnie może znaleźć oryginalnego wiersza do zaktualizowania. Można zapobiec Naruszenie współbieżności, wypełniając inny zestaw danych przy użyciu zaktualizowanych rekordów ze źródła danych, a następnie wykonuje scalania, aby zapobiec Naruszenie współbieżności. (Naruszenie współbieżności występuje, gdy inny użytkownik modyfikuje rekord w źródle danych, po napełnieniu zestawu danych.)

## <a name="update-constraints"></a>Aktualizuj ograniczenia

Aby wprowadzić zmiany do istniejącego wiersza danych, należy dodać lub zaktualizować dane w poszczególnych kolumnach. Jeśli zestaw danych zawiera ograniczeń (takich jak klucze obce lub ograniczenia innych niż null), istnieje możliwość, że rekord tymczasowo może być w stanie błędu, w przypadku aktualizowania. Oznacza to może być w stanie błędu po zakończeniu aktualizowania jedną kolumnę, ale przed zagłębieniem się do następnego.

Aby uniknąć naruszenia ograniczeń przedwczesne można czasowo zawiesić Aktualizuj ograniczenia. Służy do dwóch celów:

- Błąd uniemożliwia zgłaszane po ukończeniu aktualizacji jedną kolumnę, ale nie zostały uruchomione aktualizowanie innego.

- Uniemożliwia ona niektórych aktualizacji zdarzenia, które miałyby wywoływane (zdarzenia, które są często używane do sprawdzania poprawności).

> [!NOTE]
> W formularzach Windows Forms, architektura powiązania danych, która jest wbudowana w elemencie datagrid wstrzymuje ograniczenia sprawdzania do momentu fokusu poza wierszem, a nie trzeba jawnie wywołać <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, lub <xref:System.Data.DataRow.CancelEdit%2A> metody.

Ograniczenia są automatycznie wyłączane, gdy <xref:System.Data.DataSet.Merge%2A> metoda jest wywoływana w zestawie danych. Po zakończeniu scalania, jeśli zestaw danych, który nie może być włączone, wszelkie ograniczenia <xref:System.Data.ConstraintException> zgłaszany. W takiej sytuacji <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość jest ustawiona na `false,` i wszystkie naruszenia ograniczeń muszą zostać rozwiązane przed zresetowaniem <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość `true`.

Po zakończeniu aktualizacji, można ponownie włączyć ograniczenia sprawdzania, który również ponownie włączy zdarzeń aktualizacji i podnosi je.

Aby uzyskać więcej informacji na temat zdarzeń, zobacz [wyłączanie ograniczeń podczas zapełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Błędy aktualizacji zestawu danych

Po zaktualizowaniu rekordu w zestawie danych, istnieje prawdopodobieństwo wystąpienia błędu. Na przykład przypadkowo może zapisać danych niewłaściwy typ dla kolumny, lub danych, który jest za długi lub dane, które ma jakiś inny problem integralności. Lub, Niewykluczone, że sprawdzanie poprawności specyficznych dla aplikacji, które może wywoływać błędy niestandardowe dowolnym etapie zdarzenie aktualizacji. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Obsługa informacji na temat zmian

Informacje o zmianach wprowadzonych w zestawie danych są obsługiwane na dwa sposoby:, oznaczając flagą wierszy, które wskazują, że zostały zmienione (<xref:System.Data.DataRow.RowState%2A>), a przez przechowywanie wielu kopii rekordu (<xref:System.Data.DataRowVersion>). Korzystając z tych informacji, procesów można określić, co zmieniło się w zestawie danych i wysłać odpowiednie aktualizacje w źródle danych.

### <a name="rowstate-property"></a>Właściwość RowState

<xref:System.Data.DataRow.RowState%2A> Właściwość <xref:System.Data.DataRow> obiekt jest wartością, która zawiera informacje o stanie określonego wiersza danych.

W poniższej tabeli przedstawiono możliwe wartości <xref:System.Data.DataRowState> wyliczenia:

|Wartość właściwością DataRowState|Opis|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|Wiersz został dodany jako element, aby <xref:System.Data.DataRowCollection>. (Wiersz, w tym stanie nie ma odpowiedniej wersji oryginalnej, ponieważ nie istnieje podczas ostatniego <xref:System.Data.DataRow.AcceptChanges%2A> wywołano metodę).|
|<xref:System.Data.DataRowState.Deleted>|Wiersz został usunięty, za pomocą <xref:System.Data.DataRow.Delete%2A> z <xref:System.Data.DataRow> obiektu.|
|<xref:System.Data.DataRowState.Detached>|Wiersz został utworzony, ale nie jest częścią żadnego <xref:System.Data.DataRowCollection>. A <xref:System.Data.DataRow> obiekt jest w tym stanie, natychmiast po jego utworzeniu, zanim dodano go do kolekcji, a po jego usunięciu z kolekcji.|
|<xref:System.Data.DataRowState.Modified>|Wartość w kolumnie w wierszu została zmieniona w inny sposób.|
|<xref:System.Data.DataRowState.Unchanged>|Wiersz nie zmienił się od <xref:System.Data.DataRow.AcceptChanges%2A> ostatnio została wywołana.|

### <a name="datarowversion-enumeration"></a>Wyliczenie DataRowVersion

Zestawy danych, obsługa wielu wersji rekordów. <xref:System.Data.DataRowVersion> Pola są używane podczas pobierania wartości znalezione w <xref:System.Data.DataRow> przy użyciu <xref:System.Data.DataRow.Item%2A> właściwości lub <xref:System.Data.DataRow.GetChildRows%2A> metody <xref:System.Data.DataRow> obiektu.

W poniższej tabeli przedstawiono możliwe wartości <xref:System.Data.DataRowVersion> wyliczenia:

|Wartość DataRowVersion|Opis|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|Bieżąca wersja rekord zawiera wszystkich modyfikacjach, które zostały wykonane na rekord od czasu ostatniego <xref:System.Data.DataRow.AcceptChanges%2A> została wywołana. Wiersz został usunięty, czy nie bieżącej wersji.|
|<xref:System.Data.DataRowVersion.Default>|Wartość domyślna rekord, zgodnie z definicją schematu lub dane źródło zestawu danych.|
|<xref:System.Data.DataRowVersion.Original>|Oryginalną wersję rekordu jest kopia rekordu, jak to było dosyć ostatnie zmiany czasu zostały zatwierdzone w zestawie danych. W praktyce jest to zazwyczaj wersji rekordu jako przeczytane ze źródła danych.|
|<xref:System.Data.DataRowVersion.Proposed>|Wersja proponowana rekordu, który jest dostępny, tymczasowo w przypadku, gdy jesteś w trakcie aktualizacji — czyli w czasie między wywołana <xref:System.Data.DataRow.BeginEdit%2A> metody i <xref:System.Data.DataRow.EndEdit%2A> metody. Zwykle dostęp proponowane wersji rekordu w obsłudze zdarzeń takich jak <xref:System.Data.DataTable.RowChanging>. Wywoływanie <xref:System.Data.DataRow.CancelEdit%2A> metoda odwraca zmiany i usuwa wersja proponowana wiersza danych.|

Wersje pierwotnym i bieżącym są przydatne informacje dotyczące aktualizacji są przesyłane do źródła danych. Zazwyczaj gdy aktualizacja jest wysyłane do źródła danych, nowe informacje o bazie danych jest w bieżącej wersji rekordu. Informacje z wersją oryginalną jest używana do lokalizowania rekordu do zaktualizowania.

Na przykład w przypadku, gdy klucz podstawowy rekord zostanie zmieniony, należy to sposób zlokalizuj właściwy rekord w źródle danych, aby można było zaktualizować zmiany. Jeśli nie oryginalna wersja istnieje, a następnie rekord najprawdopodobniej zostanie dołączona do źródła danych, co nie tylko w bardzo niechciane rekordu, ale w jeden rekord, który jest niedokładna i nieaktualny. Dwie wersje są również używane w kontroli współbieżności. Możesz porównać oryginalnej wersji względem rekordu w źródle danych, aby ustalić, czy rekord został zmieniony od momentu załadowania do zestawu danych.

Wersja proponowana jest przydatne, gdy trzeba wykonać sprawdzanie poprawności przed faktycznie zatwierdzeniem zmiany do zestawu danych.

Nawet jeśli rekordy uległy zmianie, istnieje nie zawsze są oryginalnej lub bieżącej wersji tego wiersza. Podczas wstawiania nowego wiersza w tabeli, wersja nie jest oryginalne, bieżącej wersji. Podobnie można usunąć wiersza, wywołując w tabeli `Delete` metody ma oryginalną wersję, ale nie bieżącej wersji.

Możesz sprawdzić, czy określoną wersję rekord istnieje, badając wiersz danych <xref:System.Data.DataRow.HasVersion%2A> metody. Dostęp do obu wersji rekordu, przekazując <xref:System.Data.DataRowVersion> wartość wyliczenia jako opcjonalny argument, gdy użytkownik zażąda wartość kolumny.

## <a name="get-changed-records"></a>Pobieranie zmienionych rekordów

Jest to powszechną praktyką nie można zaktualizować każdego rekordu w zestawie danych. Na przykład użytkownik może działać z formularzami Windows <xref:System.Windows.Forms.DataGridView> formant, który wyświetla wiele rekordów. Jednak użytkownik może zaktualizować tylko kilka rekordów, Usuń jedno i wstawić nową. Zestawy danych i tabel danych czasu obsługi udostępniają metodę (`GetChanges`) dla zwracania tylko wiersze, które zostały zmodyfikowane.

Możesz utworzyć podzestawy zmienionych rekordów przy użyciu `GetChanges` metoda tabelę danych (<xref:System.Data.DataTable.GetChanges%2A>) lub zestawu danych (<xref:System.Data.DataSet.GetChanges%2A>) sam. Jeśli metoda jest wywołana dla tabeli danych, zwraca kopię tabeli zawierającej tylko zmienionych rekordów. Podobnie jeśli metoda jest wywołana w zestawie danych, zostanie wyświetlony nowy zestaw danych za pomocą tylko zmienionych rekordów w nim.

`GetChanges` samodzielnie rekordy wszystkie zmienione. Z kolei przekazując żądaną <xref:System.Data.DataRowState> jako parametr do `GetChanges` metody, można określić podzbiór zmienionych rekordów, które mają: nowo dodane rekordy, rekordy, które zostały oznaczone do usunięcia, odłączony rekordów lub zmodyfikowanych rekordów.

Wprowadzenie podzestaw zmienionych rekordów jest przydatne w przypadku, gdy użytkownik chce przesłać rekordów do innego składnika do przetworzenia. Zamiast przesyłania całego zestawu danych, można zmniejszyć koszty komunikowania się z innego składnika przez pobieranie tylko rekordy, które wymaga składnika.

## <a name="commit-changes-in-the-dataset"></a>Zatwierdź zmiany w zestawie danych

Zmiany w zestawie danych, <xref:System.Data.DataRow.RowState%2A> ustawiono właściwość zmienionych wierszy. Ustanowionych, przechowywane i udostępniane przez pierwotnym i bieżącym wersje rekordów <xref:System.Data.DataRowView.RowVersion%2A> właściwości. Metadane, które są przechowywane we właściwościach tych zmienionych wierszy jest niezbędne do wysyłania właściwe aktualizacje w źródle danych.

Jeśli zmiany odzwierciedlają aktualny stan źródła danych, nie będzie trzeba utrzymywać te informacje. Zazwyczaj istnieją dwa razy podczas zestawu danych i jego źródło są zsynchronizowane:

- Natychmiast po zakończeniu informacje zostały załadowane do zestawu danych, np. podczas odczytu danych ze źródła.

- Po wysłaniu zmiany z zestawu danych do źródła danych (ale nie przed ponieważ utracisz informacje zmiany, które są wymagane, aby wysłać zmiany z bazą danych).

Możesz zatwierdzić oczekujące zmiany do zestawu danych, wywołując <xref:System.Data.DataSet.AcceptChanges%2A> metody. Zazwyczaj <xref:System.Data.DataSet.AcceptChanges%2A> nazywa się o następujących godzinach:

- Po zakończeniu ładowania zestawu danych. Jeśli załadujesz zestawu danych, przez wywołanie metody TableAdapter `Fill` metody, a następnie kartę automatycznie zatwierdza zmiany za Ciebie. Jednakże jeśli zestaw danych jest załadowany przez scalenie inny zestaw danych, następnie należy ręcznie zatwierdzić zmiany.

    > [!NOTE]
    > Można zapobiec automatycznego zatwierdzania zmian po wywołaniu przez adapter `Fill` metody, ustawiając `AcceptChangesDuringFill` właściwości karty do `false`. Jeśli jest równa `false`, a następnie <xref:System.Data.DataRow.RowState%2A> każdego wiersza, który jest wstawiany podczas wypełnienia ustawiono <xref:System.Data.DataRowState.Added>.

- Po wysłaniu zmian w zestawie do innego procesu, takich jak usługi sieci web XML.

    > [!CAUTION]
    > Zatwierdzanie zmian w ten sposób usuwa wszystkie informacje o zmianach. Nie zmiany aż po zakończenia wykonywania operacji, które wymagają aplikacji w taki sposób, aby dowiedzieć się, jakie zmiany zostały wprowadzone w zestawie danych.

Ta metoda wykonuje następujące czynności:

- Zapisuje <xref:System.Data.DataRowVersion.Current> wersji rekordu do jego <xref:System.Data.DataRowVersion.Original> wersji i zastępuje oryginalną wersję.

- Usuwa wszystkie wiersze gdzie <xref:System.Data.DataRow.RowState%2A> właściwość jest ustawiona na <xref:System.Data.DataRowState.Deleted>.

- Zestawy <xref:System.Data.DataRow.RowState%2A> właściwości rekordu, aby <xref:System.Data.DataRowState.Unchanged>.

<xref:System.Data.DataSet.AcceptChanges%2A> Metoda jest dostępna na trzech poziomach. Można też wywołać na <xref:System.Data.DataRow> obiekt do zatwierdzenia zmian po prostu tego wiersza. Możesz także wywołać ją na <xref:System.Data.DataTable> obiektu, aby zatwierdzić wszystkie wiersze w tabeli. Na koniec można wywołać ją na <xref:System.Data.DataSet> obiektu, aby zatwierdzić wszystkie oczekujące zmiany we wszystkich rekordach wszystkie tabele zestawu danych.

W poniższej tabeli opisano, w których zmiany zostaną zatwierdzone w oparciu o co obiekt, że metoda jest wywoływana w:

|Metoda|Wynik|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Zmiany są zatwierdzane tylko dla konkretnego wiersza.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Zmiany zostały wprowadzone na wszystkich wierszy w określonej tabeli.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Zmiany zostały wprowadzone we wszystkich wierszach we wszystkich tabelach zestawu danych.|

> [!NOTE]
> Jeśli załadujesz zestawu danych, przez wywołanie metody TableAdapter `Fill` metody, nie trzeba jawnie zaakceptować zmiany. Domyślnie `Fill` wywołania metody `AcceptChanges` metoda po jej zakończeniu, wypełnianie tabeli danych.

Powiązana metoda <xref:System.Data.DataSet.RejectChanges%2A>, cofa efekt zmiany przez skopiowanie <xref:System.Data.DataRowVersion.Original> wersji do <xref:System.Data.DataRowVersion.Current> wersji rekordów. Ustawia również <xref:System.Data.DataRow.RowState%2A> z każdego rekordu Wstecz, aby <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Sprawdzanie poprawności danych

Aby sprawdzić, czy dane w aplikacji spełnia wymagania procesów, które są przekazywane do, często musisz dodać sprawdzanie poprawności. Może to obejmować, sprawdzanie, czy wpis użytkownika w postaci jest poprawny, sprawdzanie poprawności danych, które są wysyłane do aplikacji przez inną aplikację, lub nawet sprawdzanie, czy informacje, które jest obliczana w ramach składnika znajduje się w ramach ograniczeń źródła danych i wymagań aplikacji.

Można sprawdzić poprawność danych na kilka sposobów:

- W warstwie biznesowej, dodając kod do aplikacji w taki sposób, aby sprawdzić poprawność danych. Zestaw danych jest w jednym miejscu, możesz to zrobić. Zestaw danych zawiera niektóre zalety weryfikacji zaplecza — takie jak możliwość sprawdzenia poprawności zmian, jak zmieniają się wartości kolumn i wierszy. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).

- W warstwie prezentacji przez dodawanie walidacji do formularzy. Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności w formularzach Windows Forms z danymi użytkownika](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

- W danych zaplecza, na wysyłanie danych do źródła danych — na przykład baza danych —, dzięki czemu jej o zaakceptowanie lub odrzucenie danych. Jeśli pracujesz z bazą danych, który zawiera zaawansowane funkcje służące do sprawdzania poprawności danych, a także informacje o błędzie, może to być praktyczne podejście, ponieważ można sprawdzić poprawność danych niezależnie od tego, gdzie pochodzi on z. Jednak to podejście nie może uwzględnić wymagania sprawdzania poprawności specyficznych dla aplikacji. Ponadto posiadanie źródła danych sprawdzania poprawności danych może spowodować wiele rund do źródła danych, w zależności od tego, jak ułatwia rozpoznawanie błędów sprawdzania poprawności wygenerowane przez usługę zaplecza w aplikacji.

   > [!IMPORTANT]
   > Korzystając z polecenia danych za pomocą <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> właściwość, która jest równa <xref:System.Data.CommandType.Text>, należy dokładnie sprawdzić informacje przesyłane przez klienta przed przekazaniem go do bazy danych. Złośliwi użytkownicy mogą próby wysłania przez użytkownika (wstrzyknąć) zmodyfikowany lub dodatkowych instrukcji SQL w celu uzyskania nieautoryzowanego dostępu lub uszkodzenia bazy danych. Przed przeniesieniem danych wejściowych użytkownika do bazy danych zawsze sprawdzić, czy informacje są prawidłowe. Jest najlepszym rozwiązaniem jest zawsze używaj sparametryzowanych zapytań lub procedur przechowywanych, gdy jest to możliwe.

## <a name="transmit-updates-to-the-data-source"></a>Przesyłanie aktualizacji do źródła danych

Po zmiany zostały dokonane w zestawie danych, mogą przesyłać zmiany ze źródłem danych. Najczęściej, możesz to zrobić, wywołując `Update` metodę TableAdapter (lub adapter danych). Metoda pętlę każdy rekord w tabeli danych określa, jakiego rodzaju aktualizacji jest wymagana (aktualizowania, wstawiania lub usuwania), jeśli są dostępne, a następnie uruchamia odpowiednie polecenie.

Ilustracją jak wprowadzone aktualizacje Załóżmy, że aplikacja korzysta z zestawu danych, który zawiera jednej tabeli danych. Aplikacja pobiera dwa wiersze z bazy danych. Po ich pobraniu tabeli danych w pamięci wygląda następująco:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Aplikacja zmienia stan Nancy Bator "Preferowane". W wyniku tej zmiany wartości <xref:System.Data.DataRow.RowState%2A> właściwość dla tego wiersza zmieni się z <xref:System.Data.DataRowState.Unchanged> do <xref:System.Data.DataRowState.Modified>. Wartość <xref:System.Data.DataRow.RowState%2A> pozostaje właściwości dla pierwszego wiersza <xref:System.Data.DataRowState.Unchanged>. Tabela danych wygląda teraz następująco:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Wywołania teraz aplikacji `Update` metodę transmisji zestawu danych w bazie danych. Metody, które z kolei bada każdego wiersza. Pierwszy wiersz metody przesyła Brak instrukcji SQL w bazie danych, ponieważ ten wiersz nie została zmieniona, ponieważ pierwotnie została pobrana z bazy danych.

Dla drugiego wiersza, jednak `Update` metoda automatycznie wywołuje polecenie poprawne dane i przekazuje go do bazy danych. Określonej składni instrukcji SQL, zależy od dialekt programu SQL Server, która jest obsługiwana przez źródłowy magazyn danych. Ale warte zauważenia są następujące cechy ogólne przesyłane instrukcję SQL:

- Przesyłane instrukcja SQL jest instrukcji UPDATE. Karta wie, że ma używać instrukcji UPDATE, ponieważ wartość <xref:System.Data.DataRow.RowState%2A> właściwość <xref:System.Data.DataRowState.Modified>.

- Przesyłane instrukcja SQL zawiera klauzulę WHERE, co oznacza, że obiekt docelowy instrukcji UPDATE wiersz gdzie `CustomerID = 'c400'`. Ta część instrukcji SELECT odróżnia wiersz docelowy od wszystkich innych, ponieważ `CustomerID` jest klucz podstawowy w tabeli docelowej. Informacje o klauzuli WHERE jest tworzony na podstawie oryginalną wersję rekordu (`DataRowVersion.Original`), w przypadku, gdy zmieniono wartości, które są wymagane do identyfikowania wiersza.

- Przesyłane instrukcja SQL zawiera klauzuli SET do ustawiania nowych wartości kolumn zmodyfikowane.

   > [!NOTE]
   > Jeśli TableAdapter `UpdateCommand` właściwość została ustawiona na nazwę procedury składowanej, karta nie konstruowania instrukcji SQL. Zamiast tego wywołuje procedurę składowaną z odpowiednimi parametrami, które są przekazywane w.

## <a name="pass-parameters"></a>Przekazywanie parametrów

Zazwyczaj używasz parametry do przekazania wartości dla rekordów, które mają zostać zaktualizowane w bazie danych. Gdy TableAdapter `Update` metoda uruchamia się instrukcji UPDATE, należy ją podać wartości parametrów. Pobiera wartości te `Parameters` kolekcję dla polecenia odpowiednie dane — w tym przypadku `UpdateCommand` obiektu w metodzie TableAdapter.

Jeśli wcześniej używano narzędzia programu Visual Studio można wygenerować w obrębie adaptera danych, `UpdateCommand` obiekt zawiera zbiór parametrów, które odpowiadają każdej symbol zastępczy parametru w instrukcji.

<xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> Właściwość każdego parametru odwołuje się do kolumny w tabeli danych. Na przykład `SourceColumn` właściwość `au_id` i `Original_au_id` parametrów jest ustawiona na dowolną kolumnę w tabeli danych zawiera identyfikator autora. Gdy karty `Update` uruchamia metody odczyta Autor kolumna identyfikatora z rekordu, który jest aktualizowana i wypełnia wartości w instrukcji.

W instrukcji UPDATE należy określić zarówno nowe wartości (te, które będą zapisywane do rekordu) również stare wartości (tak, aby rekord może znajdować się w bazie danych). Istnieją, w związku z tym, dwa parametry dla każdej wartości: jeden dla klauzuli SET i inna dla klauzuli WHERE. Oba parametry odczytywać dane z rekordu, która jest aktualizowana, ale staną się różne wersje wartości kolumny, na podstawie parametru <xref:System.Data.SqlClient.SqlParameter.SourceVersion> właściwości. Parametr dla klauzuli SET pobiera bieżącą wersję, a następnie parametrów dla klauzuli WHERE pobiera oryginalnej wersji.

> [!NOTE]
> Można również ustawić wartości w `Parameters` kolekcji samodzielnie w kodzie, co zwykle należy w obsłudze zdarzeń adaptera danych <xref:System.Data.DataTable.RowChanging> zdarzeń.

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](create-and-configure-tableadapters.md)
- [Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Sprawdzanie poprawności danych](validate-data-in-datasets.md)
- [Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek (WCF data services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)