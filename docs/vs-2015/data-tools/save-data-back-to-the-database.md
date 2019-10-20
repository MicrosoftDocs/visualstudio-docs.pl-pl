---
title: Zapisz dane z powrotem w bazie danych | Microsoft Docs
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
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1b1a54d8be5ab4aa9703d318d0b537deff53b6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652872"
---
# <a name="save-data-back-to-the-database"></a>Zapisywanie danych z powrotem w bazie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw danych to kopia danych znajdująca się w pamięci. W przypadku zmodyfikowania tych danych dobrym sposobem jest zapisanie tych zmian z powrotem do bazy danych. Można to zrobić na jeden z trzech sposobów:

- Wywołując jedną z `Update` metod TableAdapter

- Wywołując jedną z metod DBDirect TableAdapter

- Wywołując metodę UpdateAll na `TableAdapterManager`, którą generuje program Visual Studio, gdy zestaw danych zawiera tabele, które są powiązane z innymi tabelami w zestawie danych

  Gdy dane są powiązane z tabelami zestawu danych z kontrolkami na stronie formularza systemu Windows lub w języku XAML, architektura powiązań danych wykonuje wszystkie czynności.

  Jeśli znasz już program TableAdapters, możesz przejść bezpośrednio do jednego z następujących tematów:

|Temat|Opis|
|-----------|-----------------|
|[Wstawianie nowych rekordów do bazy danych](../data-tools/insert-new-records-into-a-database.md)|Jak wykonywać aktualizacje i wstawiać za pomocą obiektów TableAdapters lub Command|
|[Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Jak wykonywać aktualizacje za pomocą TableAdapters|
|[Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)|Jak wykonać aktualizacje z zestawu danych z co najmniej dwiema powiązanymi tabelami|
|[Obsługiwanie wyjątku współbieżności](../data-tools/handle-a-concurrency-exception.md)|Jak obsługiwać wyjątki, gdy dwóch użytkowników próbuje zmienić te same dane w bazie danych w tym samym czasie|
|[Zapisywanie danych przy użyciu transakcji](../data-tools/save-data-by-using-a-transaction.md)|Jak zapisywać dane w transakcji przy użyciu przestrzeni nazw System. Transactions i obiektu TransactionScope|
|[Zapisywanie danych w transakcji](../data-tools/save-data-in-a-transaction.md)|Jak zapisywać dane w transakcji przy użyciu przestrzeni nazw System. Transactions|
|[Zapisywanie danych w bazie danych (wiele tabel)](../data-tools/save-data-to-a-database-multiple-tables.md)|Jak edytować rekordy i zapisywać zmiany w wielu tabelach z powrotem do bazy danych|
|[Zapisywanie danych z obiektu w bazie danych](../data-tools/save-data-from-an-object-to-a-database.md)|Jak przekazać dane z obiektu, który nie znajduje się w zestawie danych, za pomocą metody TableAdapter DBDirect|
|[Zapisywanie danych za pomocą metod DBDirect adaptera TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Jak wysyłać zapytania SQL bezpośrednio do bazy danych za pomocą TableAdapter|
|[Zapisywanie zestawu danych jako kodu XML](../data-tools/save-a-dataset-as-xml.md)|Jak zapisać zestaw danych w dokumencie XML|

## <a name="two-stage-updates"></a>Aktualizacje dwuetapowe
 Aktualizacja źródła danych jest procesem dwuetapowym. Pierwszym krokiem jest aktualizacja zestawu danych przy użyciu nowych rekordów, zmienionych rekordów lub usuniętych rekordów. Jeśli aplikacja nigdy nie wyśle tych zmian z powrotem do źródła danych, zostanie zakończona aktualizacja.

 Jeśli wyślesz zmiany z powrotem do bazy danych, wymagany jest drugi krok. Jeśli nie korzystasz z formantów powiązanych z danymi, musisz ręcznie wywołać metodę Update dla tego samego TableAdapter (lub karty danych), która została użyta do wypełniania zestawu danych. Można jednak również użyć różnych kart, na przykład do przenoszenia danych z jednego źródła danych do innego lub do aktualizowania wielu źródeł danych. Jeśli nie korzystasz z powiązania danych i zapisujesz zmiany w powiązanych tabelach, musisz ręcznie utworzyć wystąpienie zmiennej klasy TableAdapterManager, a następnie wywołać metodę UpdateAll.

 ![Aktualizacje zestawu danych Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates") Dwuetapowy proces aktualizacji i rola DataRowVersion w przypadku pomyślnej aktualizacji

 Zestaw danych zawiera kolekcje tabel, które zawierają kolekcje wierszy. Jeśli zamierzasz zaktualizować bazowe źródło danych później, musisz użyć metod właściwości DataTable. DataRowcollection podczas dodawania lub usuwania wierszy. Te metody wykonują śledzenie zmian, które są niezbędne do aktualizowania źródła danych. Jeśli wywołasz kolekcję RemoveAt we właściwości Rows, usunięcie nie zostanie przekazane z powrotem do bazy danych.

## <a name="merge-datasets"></a>Scal zestawy danych
 Możesz zaktualizować zawartość zestawu danych, *scalając* go z innym zestawem danych. Obejmuje to kopiowanie zawartości *źródłowego* zestawu danych do wywołującego zestawu danych (określanego jako *docelowy* zestaw danych). Gdy scalasz zestawy danych, nowe rekordy w źródłowym zestawie danych są dodawane do docelowego zestawu danych. Ponadto dodatkowe kolumny w źródłowym zestawie danych są dodawane do docelowego zestawu danych. Scalanie zestawów danych jest przydatne, gdy posiadasz lokalny DataSet i uzyskasz drugi zestaw danych z innej aplikacji. Jest on również przydatny, gdy pobierasz drugi zestaw danych z składnika, takiego jak usługa sieci Web XML, lub gdy musisz zintegrować dane z wielu zestawów danych.

 Podczas scalania zestawów danych można przekazać argument logiczny (`preserveChanges`), który nakazuje <xref:System.Data.DataSet.Merge%2A> metody, czy zachować istniejące modyfikacje w docelowym zestawie danych. Ponieważ zestawy danych obsługują wiele wersji rekordów, ważne jest, aby pamiętać, że jest scalanych więcej niż jedna wersja rekordów. W poniższej tabeli przedstawiono sposób scalania rekordu w dwóch zestawach danych:

|DataRowVersion|Docelowy zestaw danych|Źródłowy zestaw danych|
|--------------------|--------------------|--------------------|
|Oryginał|Kuba Wilson|Kuba C. Wilson|
|Obecne|Jim Wilson|Kuba C. Wilson|

 Wywołanie metody <xref:System.Data.DataSet.Merge%2A> w poprzedniej tabeli z `preserveChanges=false targetDataset.Merge(sourceDataset)` powoduje następujące czynności:

|DataRowVersion|Docelowy zestaw danych|Źródłowy zestaw danych|
|--------------------|--------------------|--------------------|
|Oryginał|Kuba C. Wilson|Kuba C. Wilson|
|Obecne|Kuba C. Wilson|Kuba C. Wilson|

 Wywołanie metody <xref:System.Data.DataSet.Merge%2A> z `preserveChanges = true targetDataset.Merge(sourceDataset, true)` powoduje następujące czynności:

|DataRowVersion|Docelowy zestaw danych|Źródłowy zestaw danych|
|--------------------|--------------------|--------------------|
|Oryginał|Kuba C. Wilson|Kuba C. Wilson|
|Obecne|Jim Wilson|Kuba C. Wilson|

> [!CAUTION]
> W scenariuszu `preserveChanges = true`, jeśli metoda <xref:System.Data.DataSet.RejectChanges%2A> jest wywoływana dla rekordu w docelowym zestawie danych, przywraca oryginalne dane ze *źródłowego* zestawu danych. Oznacza to, że w przypadku próby zaktualizowania oryginalnego źródła danych za pomocą docelowego zestawu danych może nie być możliwe znalezienie oryginalnego wiersza do zaktualizowania. Można zapobiec naruszeniu współbieżności, wypełniając inny zestaw danych ze zaktualizowanymi rekordami ze źródła danych, a następnie wykonując scalanie, aby zapobiec naruszeniu współbieżności. (Naruszenie współbieżności występuje, gdy inny użytkownik modyfikuje rekord w źródle danych po wypełnieniu zestawu danych).

## <a name="update-constraints"></a>Ograniczenia aktualizacji
 Aby wprowadzić zmiany w istniejącym wierszu danych, Dodaj lub zaktualizuj dane w poszczególnych kolumnach. Jeśli zestaw danych zawiera ograniczenia (takie jak klucze obce lub ograniczenia niedopuszczające wartości null), istnieje możliwość, że rekord może być tymczasowo w stanie błędu podczas jego aktualizowania. Oznacza to, że może być w stanie błędu po zakończeniu aktualizowania jednej kolumny, ale przed przejściem do następnej.

 Aby zapobiec naruszeniu niedojrzałych ograniczeń, można tymczasowo zawiesić ograniczenia aktualizacji. Służy do tego dwa cele:

- Uniemożliwia to Zgłaszanie błędu po zakończeniu aktualizowania jednej kolumny, ale nie rozpoczęto aktualizowania drugiej.

- Uniemożliwia to wywoływanie niektórych zdarzeń aktualizacji (zdarzenia, które są często używane do walidacji).

  Po ukończeniu aktualizacji można ponownie włączyć sprawdzanie ograniczeń, co spowoduje również ponowne włączenie zdarzeń aktualizacji i ich podwyższenie.

> [!NOTE]
> W Windows Forms architektura powiązania danych, która jest wbudowana w element DataGrid, zawiesza sprawdzanie ograniczeń, dopóki fokus nie zostanie przeniesiony poza wiersz i nie trzeba jawnie wywoływać <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> lub <xref:System.Data.DataRow.CancelEdit%2A> metod.

 Ograniczenia są automatycznie wyłączane, gdy metoda <xref:System.Data.DataSet.Merge%2A> jest wywoływana na zestawie danych. Gdy Scalanie zostanie ukończone, jeśli istnieją jakiekolwiek ograniczenia dotyczące zestawu danych, którego nie można włączyć, zostanie zgłoszony <xref:System.Data.ConstraintException>. W tej sytuacji Właściwość <xref:System.Data.DataSet.EnforceConstraints%2A> jest ustawiona na `false,` i wszystkie naruszenia ograniczenia muszą zostać rozwiązane przed zresetowaniem właściwości <xref:System.Data.DataSet.EnforceConstraints%2A> do `true`.

 Po ukończeniu aktualizacji można ponownie włączyć sprawdzanie ograniczeń, co spowoduje również ponowne włączenie zdarzeń aktualizacji i ich podwyższenie.

 Aby uzyskać więcej informacji na temat wstrzymywania zdarzeń, zobacz Wyłączanie [ograniczeń podczas wypełniania zestawu danych](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Błędy aktualizacji zestawu danych
 W przypadku aktualizowania rekordu w zestawie danych istnieje możliwość błędu. Na przykład można przypadkowo zapisywać dane niewłaściwego typu do kolumny lub dane, które są zbyt długie, lub dane, które mają inny problem z integralnością. Lub można sprawdzić sprawdzanie poprawności specyficzne dla aplikacji, które mogą zgłaszać błędy niestandardowe na dowolnym etapie zdarzenia aktualizacji. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych w zestawach DataSet](../data-tools/validate-data-in-datasets.md).

## <a name="maintaining-information-about-changes"></a>Obsługa informacji o zmianach
 Informacje o zmianach w zestawie danych są obsługiwane na dwa sposoby: przez Oflagowanie wierszy, które wskazują, że zostały zmienione (<xref:System.Data.DataRow.RowState%2A>) i przez przechowywanie wielu kopii rekordu (<xref:System.Data.DataRowVersion>). Korzystając z tych informacji, procesy mogą określić, co zostało zmienione w zestawie danych i które można wysłać odpowiednie aktualizacje do źródła danych.

### <a name="rowstate-property"></a>Właściwość RowState
 Właściwość <xref:System.Data.DataRow.RowState%2A> obiektu <xref:System.Data.DataRow> jest wartością, która zawiera informacje o stanie określonego wiersza danych.

 Poniższa tabela zawiera szczegółowe informacje na temat możliwych wartości <xref:System.Data.DataRowState> Wyliczenie:

|DataRowState wartość|Opis|
|------------------------|-----------------|
|<xref:System.Data.DataRowState>|Wiersz został dodany jako element do <xref:System.Data.DataRowCollection>. (Wiersz w tym stanie nie ma odpowiadającej oryginalnej wersji, ponieważ nie istniał w momencie wywołania ostatniej metody <xref:System.Data.DataRow.AcceptChanges%2A>).|
|<xref:System.Data.DataRowState>|Wiersz został usunięty przy użyciu <xref:System.Data.DataRow.Delete%2A> obiektu <xref:System.Data.DataRow>.|
|<xref:System.Data.DataRowState>|Wiersz został utworzony, ale nie jest częścią żadnego <xref:System.Data.DataRowCollection>. Obiekt <xref:System.Data.DataRow> jest w tym stanie zaraz po jego utworzeniu, zanim zostanie dodany do kolekcji, a następnie usunięty z kolekcji.|
|<xref:System.Data.DataRowState>|Wartość kolumny w wierszu zmieniła się w jakiś sposób.|
|<xref:System.Data.DataRowState>|Wiersz nie został zmieniony od czasu ostatniego wywołania <xref:System.Data.DataRow.AcceptChanges%2A>.|

### <a name="datarowversion-enumeration"></a>DataRowVersion, Wyliczenie
 Zestawy danych obsługują wiele wersji rekordów. Wyliczenie <xref:System.Data.DataRowVersion> obiektu <xref:System.Data.DataRow> jest wartością, której można użyć do zwrócenia określonej wersji obiektu <xref:System.Data.DataRow>.

 Poniższa tabela zawiera szczegółowe informacje na temat możliwych wartości <xref:System.Data.DataRowVersion> Wyliczenie:

|DataRowVersion wartość|Opis|
|--------------------------|-----------------|
|<xref:System.Data.DataRowVersion>|Bieżąca wersja rekordu zawiera wszystkie modyfikacje, które zostały wykonane względem rekordu od czasu ostatniego wywołania <xref:System.Data.DataRow.AcceptChanges%2A>. Jeśli wiersz został usunięty, nie ma bieżącej wersji.|
|<xref:System.Data.DataRowVersion>|Wartość domyślna rekordu, zgodnie z definicją przez schemat zestawu danych lub źródło danych.|
|<xref:System.Data.DataRowVersion>|Oryginalna wersja rekordu jest kopią rekordu, ponieważ była to Ostatnia zmiana została zatwierdzona w zestawie danych. W praktyce jest to zazwyczaj wersja rekordu jako odczytana ze źródła danych.|
|<xref:System.Data.DataRowVersion>|Proponowana wersja rekordu, która jest tymczasowo dostępna podczas pracy w trakcie aktualizacji — czyli od momentu wywołania metody <xref:System.Data.DataRow.BeginEdit%2A> i metody <xref:System.Data.DataRow.EndEdit%2A>. Zwykle uzyskujesz dostęp do proponowanej wersji rekordu w procedurze obsługi dla zdarzenia, takiego jak <xref:System.Data.DataTable.RowChanging>. Wywołanie metody <xref:System.Data.DataRow.CancelEdit%2A> powoduje odwrócenie zmian i usunięcie proponowanej wersji wiersza danych.|

 Wersje oryginalne i bieżące są przydatne, gdy informacje o aktualizacji są przesyłane do źródła danych. Zwykle, gdy aktualizacja jest wysyłana do źródła danych, nowe informacje dla bazy danych są w bieżącej wersji rekordu. Informacje z oryginalnej wersji są używane do lokalizowania rekordu do zaktualizowania.

 Na przykład w przypadku, gdy klucz podstawowy rekordu jest zmieniany, konieczne jest odnalezienie poprawnego rekordu w źródle danych w celu zaktualizowania zmian. Jeśli oryginalna wersja nie istnieje, rekord prawdopodobnie jest dołączany do źródła danych, co nie tylko w niewłaściwym rekordzie, ale w jednym rekordzie, który jest niedokładny i nieaktualny. Te dwie wersje są również używane w kontroli współbieżności. Można porównać oryginalną wersję z rekordem w źródle danych, aby określić, czy rekord został zmieniony od momentu załadowania do zestawu danych.

 Proponowana wersja jest przydatna, gdy trzeba przeprowadzić walidację przed faktycznym zatwierdzeniem zmian w zestawie danych.

 Nawet jeśli rekordy uległy zmianie, nie zawsze są oryginalne lub aktualne wersje tego wiersza. Gdy wstawisz nowy wiersz do tabeli, nie ma wersji oryginalnej, tylko dla bieżącej wersji. Podobnie, jeśli usuniesz wiersz przez wywołanie metody `Delete` tabeli, istnieje oryginalna wersja, ale nie bieżąca wersja.

 Możesz sprawdzić, czy istnieje określona wersja rekordu, badając metodę <xref:System.Data.DataRow.HasVersion%2A> wiersza danych. Możesz uzyskać dostęp do dowolnej wersji rekordu, przekazując <xref:System.Data.DataRowVersion> wartość wyliczenia jako opcjonalny argument, gdy zażądasz wartości kolumny.

## <a name="getting-changed-records"></a>Pobieranie zmienionych rekordów
 Typowym sposobem, aby nie aktualizować każdego rekordu w zestawie danych. Na przykład użytkownik może pracować z kontrolką <xref:System.Windows.Forms.DataGridView> Windows Forms, która wyświetla wiele rekordów. Jednak użytkownik może aktualizować tylko kilka rekordów, usuwać je i wstawiać nowe. Zestawy danych i tabele dane zapewniają metodę (`GetChanges`) do zwracania tylko wierszy, które zostały zmodyfikowane.

 Podzestawy zmienionych rekordów można utworzyć przy użyciu metody `GetChanges` tabeli danych (<xref:System.Data.DataTable.GetChanges%2A>) lub samego zestawu danych (<xref:System.Data.DataSet.GetChanges%2A>). Jeśli wywołasz metodę dla tabeli danych, zwróci ona kopię tabeli tylko zmienionymi rekordami. Podobnie, jeśli wywołasz metodę w zestawie danych, zostanie wyświetlony nowy zestaw danych z tylko zmienionymi rekordami.

 `GetChanges` przez siebie same zwraca wszystkie zmienione rekordy. Z kolei przez przekazanie żądanego <xref:System.Data.DataRowState> jako parametru do metody `GetChanges` można określić, jaki podzbiór zmienionych rekordów: nowo dodane rekordy, rekordy, które są oznaczone do usunięcia, odłączone rekordy lub zmodyfikowane rekordy.

 Pobieranie podzbioru zmienionych rekordów jest przydatne, gdy chcesz wysyłać rekordy do innego składnika do przetwarzania. Zamiast wysyłać cały zestaw danych, można zmniejszyć obciążenie komunikacji z drugim składnikiem, pobierając tylko te rekordy, których potrzebuje składnik. Aby uzyskać więcej informacji, zobacz [How to: pobieranie zmienionych wierszy](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

## <a name="committing-changes-in-the-dataset"></a>Zatwierdzanie zmian w zestawie danych
 Po wprowadzeniu zmian w zestawie danych zostanie ustawiona właściwość <xref:System.Data.DataRow.RowState%2A> zmienionych wierszy. Oryginalna i aktualna wersja rekordów są ustanawiane, obsługiwane i udostępniane przez właściwość <xref:System.Data.DataRowView.RowVersion%2A>. Metadane przechowywane we właściwościach tych zmienionych wierszy są niezbędne do wysłania odpowiednich aktualizacji do źródła danych.

 Jeśli zmiany odzwierciedlają bieżący stan źródła danych, nie musisz już obsługiwać tych informacji. Zazwyczaj istnieją dwa razy, gdy zestaw danych i jego źródło są zsynchronizowane:

- Natychmiast po załadowaniu informacji do zestawu danych, na przykład podczas odczytywania danych ze źródła.

- Po wysłaniu zmian z zestawu danych do źródła danych (ale nie przed, ponieważ zostałyby utracone informacje o zmianach, które są wymagane do wysłania zmian do bazy danych).

  Możesz zatwierdzić oczekujące zmiany do zestawu danych, wywołując metodę <xref:System.Data.DataSet.AcceptChanges%2A>. Zwykle <xref:System.Data.DataSet.AcceptChanges%2A> jest wywoływana w aplikacji w następujący sposób.

- Po załadowaniu zestawu danych. W przypadku ładowania zestawu danych przez wywołanie metody `Fill` TableAdapter, karta automatycznie zatwierdzi zmiany. Jednak w przypadku ładowania zestawu danych przez scalenie z nim innego zestawu danych, należy ręcznie zatwierdzić zmiany.

  > [!NOTE]
  > Można zapobiec automatycznemu zatwierdzeniu przez kartę zmian po wywołaniu metody `Fill` przez ustawienie właściwości `AcceptChangesDuringFill` karty na `false`. Jeśli jest ustawiona na `false`, wówczas <xref:System.Data.DataRow.RowState%2A> każdego wiersza wstawianego podczas wypełniania jest ustawiony na <xref:System.Data.DataRowState>.

- Po wysłaniu zmian zestawu danych do innego procesu, takiego jak usługa sieci Web XML.

  > [!CAUTION]
  > Zatwierdzenie zmiany w ten sposób spowoduje wymazanie wszelkich informacji o zmianach. Nie zatwierdzaj zmian do momentu zakończenia wykonywania operacji, które wymagają, aby aplikacja wiedziała, jakie zmiany zostały wprowadzone w zestawie danych.

  Ta metoda wykonuje następujące czynności:

- Zapisuje <xref:System.Data.DataRowVersion> wersję rekordu w wersji <xref:System.Data.DataRowVersion> i zastępuje oryginalną wersję.

- Usuwa każdy wiersz, w którym Właściwość <xref:System.Data.DataRow.RowState%2A> jest ustawiona na <xref:System.Data.DataRowState>.

- Ustawia właściwość <xref:System.Data.DataRow.RowState%2A> rekordu do <xref:System.Data.DataRowState>.

  Metoda <xref:System.Data.DataSet.AcceptChanges%2A> jest dostępna na trzech poziomach. Możesz wywołać ją na obiekcie <xref:System.Data.DataRow>, aby zatwierdzić zmiany tylko dla tego wiersza. Możesz również wywołać ją na obiekcie <xref:System.Data.DataTable>, aby zatwierdzić wszystkie wiersze w tabeli. Na koniec można wywołać go w obiekcie <xref:System.Data.DataSet>, aby zatwierdzić wszystkie zmiany oczekujące we wszystkich rekordach wszystkich tabel zestawu danych.

  W poniższej tabeli opisano, które zmiany są zatwierdzane na podstawie obiektu, w którym jest wywoływana metoda.

|Metoda|Wynik|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Zmiany są zatwierdzane tylko w konkretnym wierszu.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Zmiany są zatwierdzane dla wszystkich wierszy w określonej tabeli.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Zmiany są zatwierdzane we wszystkich wierszach we wszystkich tabelach zestawu danych.|

> [!NOTE]
> W przypadku ładowania zestawu danych przez wywołanie metody `Fill` TableAdapter nie trzeba jawnie akceptować zmian. Domyślnie metoda `Fill` wywołuje metodę `AcceptChanges` po zakończeniu wypełniania tabeli danych.

 Pokrewna Metoda, `RejectChanges`, cofa efekt zmian przez skopiowanie wersji <xref:System.Data.DataRowVersion> z powrotem do <xref:System.Data.DataRowVersion> wersji rekordów. Ustawia również <xref:System.Data.DataRow.RowState%2A> każdego rekordu z powrotem do <xref:System.Data.DataRowState>.

## <a name="data-validation"></a>Sprawdzanie poprawności danych
 Aby upewnić się, że dane w aplikacji spełniają wymagania dotyczące procesów, do których jest przenoszona, często trzeba dodać weryfikację. Może to oznaczać, że wpis użytkownika w formularzu jest poprawny, sprawdzanie poprawności danych wysyłanych do aplikacji przez inną aplikację, a nawet sprawdzanie, czy informacje obliczane w składniku są objęte ograniczeniami źródła danych i wymagania aplikacji.

 Możesz sprawdzić poprawność danych na kilka sposobów:

- W warstwie biznesowej przez dodanie kodu do aplikacji w celu zweryfikowania danych. Zestaw danych to jedno miejsce, w którym można to zrobić. Projektant obiektów DataSet zapewnia pewne zalety weryfikacji zaplecza, takie jak możliwość sprawdzania poprawności zmian w miarę zmieniania wartości kolumn i wierszy. Aby uzyskać więcej informacji, zobacz [Weryfikowanie danych w zestawach DataSet](../data-tools/validate-data-in-datasets.md).

- W warstwie prezentacji przez dodanie walidacji do formularzy. Aby uzyskać więcej informacji, zobacz [walidacja danych wejściowych użytkownika w Windows Forms](https://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1).

- W zapleczu danych przez wysłanie danych do źródła danych, na przykład bazy danych — i umożliwienie mu akceptowania lub odrzucania danych. Jeśli pracujesz z bazą danych, która ma zaawansowane funkcje do sprawdzania poprawności danych i zapewniania informacji o błędach, może to być praktyczne podejście, ponieważ można zweryfikować dane niezależnie od tego, skąd pochodzą. Jednak takie podejście może nie uwzględniać wymagań związanych z walidacją specyficzną dla aplikacji. Ponadto, jeśli źródło danych sprawdza poprawność danych, może to spowodować liczne podróże do źródła danych, w zależności od tego, w jaki sposób aplikacja ułatwia rozwiązywanie błędów walidacji zgłoszonych przez zaplecze.

  > [!IMPORTANT]
  > W przypadku używania poleceń danych z właściwością <xref:System.Data.SqlClient.SqlCommand.CommandType%2A>, która jest ustawiona na <xref:System.Data.CommandType>, należy uważnie sprawdzić informacje wysyłane z klienta przed przekazaniem go do bazy danych. Złośliwi użytkownicy mogą próbować wysyłać (wstrzyknąć) zmodyfikowane lub dodatkowe instrukcje SQL w celu uzyskania nieautoryzowanego dostępu lub uszkodzenia bazy danych. Przed przeniesieniem danych wejściowych użytkownika do bazy danych programu należy zawsze sprawdzić, czy informacje są prawidłowe. Najlepszym rozwiązaniem jest zawsze używanie sparametryzowanych zapytań lub procedur składowanych, gdy jest to możliwe. Aby uzyskać więcej informacji, zobacz [Omówienie luk w zabezpieczeniach](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).

  Po wprowadzeniu zmian w zestawie danych można przesłać zmiany do źródła danych. Najczęściej jest to spowodowane wywołaniem metody `Update` TableAdapter (lub adapter danych). Metoda powoduje pętlę przez każdy rekord w tabeli danych, określa, jakiego typu aktualizacja jest wymagana (Update, INSERT lub Delete), jeśli istnieje, a następnie uruchamia odpowiednie polecenie.

## <a name="transmitting-updates-to-the-data-source"></a>Przesyłanie aktualizacji do źródła danych
 Jak widać aktualizacje, Załóżmy, że aplikacja korzysta z zestawu danych, który zawiera pojedynczą tabelę danych. Aplikacja pobiera dwa wiersze z bazy danych. Po pobraniu tabela danych znajdująca się w pamięci wygląda następująco:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

 Twoja aplikacja zmienia status Nancy Buchanan na "preferowane". W wyniku tej zmiany wartość właściwości <xref:System.Data.DataRow.RowState%2A> dla tego wiersza zmienia się z <xref:System.Data.DataRowState> na <xref:System.Data.DataRowState>. Wartość właściwości <xref:System.Data.DataRow.RowState%2A> pierwszego wiersza pozostaje <xref:System.Data.DataRowState>. Tabela danych wygląda teraz następująco:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

 Aplikacja teraz wywołuje metodę `Update`, aby przesłać zestaw danych do bazy danych. Metoda sprawdza każdy wiersz z kolei. Dla pierwszego wiersza Metoda przesyła bez instrukcji SQL do bazy danych, ponieważ ten wiersz nie został zmieniony od czasu pierwotnego pobrania z bazy danych.

 Jednak w drugim wierszu Metoda `Update` automatycznie wywołuje poprawne polecenie danych i przesyła je do bazy danych. Określona składnia instrukcji SQL zależy od dialektu SQL obsługiwanego przez podstawowy magazyn danych. Jednak następujące ogólne cechy przesyłanej instrukcji SQL są dostępne:

- Przesłana instrukcja SQL jest instrukcją UPDATE. Adapter wie, aby użyć instrukcji UPDATE, ponieważ wartość właściwości <xref:System.Data.DataRow.RowState%2A> jest <xref:System.Data.DataRowState>.

- Przesłana instrukcja SQL zawiera klauzulę WHERE wskazującą, że obiektem docelowym instrukcji UPDATE jest wiersz, w którym `CustomerID = 'c400'`. Ta część instrukcji SELECT odróżnia wiersz docelowy od wszystkich innych, ponieważ `CustomerID` jest kluczem podstawowym tabeli docelowej. Informacje dla klauzuli WHERE są wyprowadzane z oryginalnej wersji rekordu (`DataRowVersion.Original`), na wypadek gdyby wartości, które są wymagane do zidentyfikowania wiersza, uległy zmianie.

- Przesłana instrukcja SQL zawiera klauzulę SET, aby ustawić nowe wartości modyfikowanych kolumn.

    > [!NOTE]
    > Jeśli właściwość `UpdateCommand` TableAdapter została ustawiona na nazwę procedury składowanej, karta nie konstruuje instrukcji SQL. Zamiast tego wywołuje procedurę przechowywaną z odpowiednimi parametrami.

## <a name="passing-parameters"></a>Przekazywanie parametrów
 Zwykle parametry są używane do przekazywania wartości dla rekordów, które mają zostać zaktualizowane w bazie danych.  Gdy metoda `Update` TableAdapter uruchamia instrukcję UPDATE, musi wypełnić wartości parametrów. Pobiera te wartości z kolekcji `Parameters` dla odpowiednich poleceń danych — w tym przypadku `UpdateCommand` obiekt w TableAdapter.

 Jeśli użyto narzędzi Visual Studio Tools do wygenerowania adaptera danych, obiekt `UpdateCommand` zawiera kolekcję parametrów odpowiadającą każdemu symbolowi zastępczemu parametru w instrukcji.

 Właściwość <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> każdego parametru wskazuje kolumnę w tabeli danych. Na przykład właściwość `SourceColumn` dla parametrów `au_id` i `Original_au_id` jest ustawiona na dowolną kolumnę w tabeli danych, która zawiera identyfikator autora. Po uruchomieniu metody `Update` adaptera odczytuje kolumnę ID autora z rekordu, który jest aktualizowany, i wypełnia wartości do instrukcji.

 W instrukcji UPDATE należy określić zarówno nowe wartości (te, które będą zapisywane w rekordzie) jak i stare wartości (tak, aby rekord mógł znajdować się w bazie danych). W związku z tym dwa parametry dla każdej wartości: jeden dla klauzuli SET i inny dla klauzuli WHERE. Oba parametry odczytują dane ze zaktualizowanego rekordu, ale uzyskują różne wersje wartości kolumny na podstawie [Właściwości SqlParameter. SourceVersion](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx)parametru. Parametr dla klauzuli SET pobiera bieżącą wersję, a parametr klauzuli WHERE pobiera oryginalną wersję.

> [!NOTE]
> Możesz również ustawić wartości w kolekcji `Parameters` samodzielnie w kodzie, co zwykle można wykonać przy użyciu programu obsługi zdarzeń dla zdarzenia <xref:System.Data.DataTable.RowChanging> karty danych.

## <a name="see-also"></a>Zobacz też
 [Aktualizowanie danych przy użyciu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) [przygotowanie aplikacji do odbierania](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [formantów powiązań danych do danych w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) [Sprawdzanie poprawności danych](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
