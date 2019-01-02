---
title: Tworzenie zapytań względem zestawów danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: b3b51946c9fbf6ba38249c8ca7056179b58ee8a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852495"
---
# <a name="query-datasets"></a>Tworzenie zapytań względem zestawów danych
Aby wyszukać konkretne rekordy w zestawie danych, należy użyć `FindBy` metody w elemencie DataTable pisania własnych instrukcji foreach do pętli kolekcji wierszy w tabeli lub użyj [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Rozróżnianie wielkości liter dla zestawu danych
W zestawie danych, nazwy tabel i kolumn domyślnie wielkość liter — oznacza to, tabeli w zestawie danych o nazwie "Klienci" może również określane jako "klientów." Odpowiada to konwencje nazewnictwa w wielu bazach danych, w tym program SQL Server. W programie SQL Server domyślne zachowanie to, że nazwy elementów danych nie mogą być wyodrębnione tylko wielkością liter.

> [!NOTE]
>  W przeciwieństwie do zestawów danych dokumentów XML jest rozróżniana wielkość liter, więc nazwy elementów danych zdefiniowanych w schematach jest rozróżniana wielkość liter. Na przykład protokół schemat umożliwia schematu do definiowania tabeli o nazwie "Klientów" i inną tabelę o nazwie "klientów." Może to spowodować Kolizje nazw podczas schematu, który zawiera elementy, które różnią się tylko wielkością liter jest używany do generowania klasy dataset.

Wielkość liter, jednak może być czynnikiem, w jaki sposób interpretowania danych w zestawie danych. Na przykład w możesz filtrować dane w tabeli zestawu danych, kryteria wyszukiwania mogą zwracać różne wyniki w zależności od tego, czy wynikiem porównania jest uwzględniana wielkość liter. Można kontrolować rozróżnianie wielkości liter, filtrowanie, wyszukiwanie i sortowanie według ustawienia zestawu danych <xref:System.Data.DataSet.CaseSensitive%2A> właściwości. Domyślnie wszystkie tabele w zestawie danych dziedziczą wartość tej właściwości. (Można zastąpić tę właściwość, dla każdej pojedynczej tabeli, ustawiając w tabeli <xref:System.Data.DataTable.CaseSensitive%2A> właściwości.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Lokalizowanie określonego wiersza w tabeli danych

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Aby znaleźć wiersza w zestawie danych wpisywanych za pomocą wartości klucza podstawowego

-   Aby zlokalizować wiersza, należy wywołać silnie typizowaną `FindBy` metody, która używa klucza podstawowego tabeli.

     W poniższym przykładzie `CustomerID` kolumna jest klucz podstawowy `Customers` tabeli. Oznacza to, że wygenerowany `FindBy` metodą jest `FindByCustomerID`. W przykładzie pokazano, jak przypisać określonego <xref:System.Data.DataRow> do zmiennej za pomocą wygenerowany `FindBy` metody.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Aby odnaleźć wiersza nietypizowany zestaw danych o wartości klucza podstawowego

-   Wywołaj <xref:System.Data.DataRowCollection.Find%2A> metody <xref:System.Data.DataRowCollection> kolekcji, przekazując klucz podstawowy, jako parametr.

     Poniższy przykład pokazuje sposób deklarowania nowego wiersza, o nazwie `foundRow` i przypisz mu wartość zwracaną przez <xref:System.Data.DataRowCollection.Find%2A> metody. Jeśli zostanie znaleziony klucza podstawowego, zawartość 1. indeks kolumny są wyświetlane w oknie komunikatu.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Znajdź wiersz według wartości w kolumnie

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Aby znaleźć wiersze na podstawie wartości w dowolnej kolumnie

-   Tabele danych są tworzone za pomocą <xref:System.Data.DataTable.Select%2A> metody, która zwraca tablicę <xref:System.Data.DataRow>s oparte na wyrażeniu przekazany do <xref:System.Data.DataTable.Select%2A> metody. Aby uzyskać więcej informacji na temat tworzenia prawidłowych wyrażeń, zobacz sekcję "Składni wyrażenia" strony <xref:System.Data.DataColumn.Expression%2A> właściwości.

     Poniższy przykład pokazuje, jak używać <xref:System.Data.DataTable.Select%2A> metody <xref:System.Data.DataTable> zlokalizować określonych wierszy.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Dostęp do powiązanych rekordów
W przypadku tabel w zestawie danych są powiązane, <xref:System.Data.DataRelation> obiektu można udostępnić powiązanych rekordów w innej tabeli. Na przykład zestaw danych zawierający `Customers` i `Orders` tabele mogą być udostępniane.

Możesz użyć <xref:System.Data.DataRelation> obiekt do zlokalizowania rekordy pokrewne, wywołując <xref:System.Data.DataRow.GetChildRows%2A> metody <xref:System.Data.DataRow> w tabeli nadrzędnej. Ta metoda zwraca tablicę powiązane rekordy podrzędne. Ewentualnie możesz wywołać <xref:System.Data.DataRow.GetParentRow%2A> metody <xref:System.Data.DataRow> w tabeli podrzędnej. Ta metoda zwraca pojedynczą <xref:System.Data.DataRow> z tabeli nadrzędnej.

Ta strona zawiera przykłady użycia typizowanych zestawów danych. Aby dowiedzieć się, jak nawigowanie po relacjach w nietypizowane zbiory danych, zobacz [przejść elementów DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
>  Jeśli pracujesz w aplikacji Windows Forms i przy użyciu funkcji wiązania danych, aby wyświetlić dane, wygenerowany przez projektanta formularzy może zapewnić wystarczającą ilość funkcjonalność dla aplikacji. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). W szczególności zobacz [relacje w zestawach danych](relationships-in-datasets.md).

Poniższe przykłady kodu pokazują, jak poruszać się po relacjach w typizowanych zestawów danych. Użyj przykłady kodu wpisane <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) i wygenerowanego FindBy*PrimaryKey* (`FindByCustomerID`) metody znajdź żądany wiersz i zwracać powiązanych rekordów. Przykłady skompilować i uruchomić się poprawnie, tylko wtedy, gdy masz:

-   Wystąpienie zestawu danych o nazwie `NorthwindDataSet` z `Customers` tabeli.

-   `Orders` Tabeli.

-   Relacji o nazwie `FK_Orders_Customers`odnoszących się dwie tabele.

Ponadto obie tabele muszą zostać wypełnione danymi dla rekordów do zwrócenia.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Aby powrócić podrzędne rekordy wybrany rekord nadrzędny

-   Wywołaj <xref:System.Data.DataRow.GetChildRows%2A> metody określonej `Customers` danych wiersza, a następnie zwraca tablicę wiersze z `Orders` tabeli:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Aby przywrócić rekord nadrzędny wybranego podrzędnego rekordu

-   Wywołaj <xref:System.Data.DataRow.GetParentRow%2A> metody określonej `Orders` wiersz danych i zwrócenia pojedynczy wiersz z tabeli `Customers` tabeli:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)