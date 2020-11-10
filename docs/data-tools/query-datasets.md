---
title: Tworzenie zapytań względem zestawów danych
description: Omówienie zestawów danych zapytań. Dowiedz się więcej o rozróżnianiu wielkości liter w zestawie danych. Znajdź konkretny wiersz w tabeli danych, Znajdź wiersze według wartości kolumn i rekordy powiązane z dostępem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8ccf228b147301eb9fccf41da98f8cc5204971a9
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436071"
---
# <a name="query-datasets"></a>Tworzenie zapytań względem zestawów danych
Aby wyszukać określone rekordy w zestawie danych, należy użyć `FindBy` metody z tabeli DataTable, napisać własną instrukcję foreach do pętli w kolekcji Rows tabel lub użyć [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Rozróżnianie wielkości liter dla zestawu danych
W ramach zestawu danych nazwy tabel i kolumn są domyślnie bez uwzględniania wielkości liter — to znaczy, że tabela w zestawie danych o nazwie "Customers" może być również określana jako "Customers". Jest to zgodne z konwencjami nazewnictwa w wielu bazach danych, w tym SQL Server. W SQL Server domyślnym zachowaniem jest to, że nazwy elementów danych nie mogą być wyróżniane tylko wielkością liter.

> [!NOTE]
> W przeciwieństwie do zestawów danych dokumenty XML są rozróżniane wielkości liter, więc nazwy elementów danych zdefiniowane w schematach uwzględniają wielkość liter. Na przykład protokół schematu pozwala schematowi definiować tabelę o nazwie "Customers" i inną tabelę o nazwie "Customers". Może to powodować kolizje nazw, gdy schemat zawierający elementy, które różnią się tylko wielkością liter, jest używany do generowania klasy DataSet.

Jednak uwzględnianie wielkości liter może być czynnikiem, w jaki dane są interpretowane w zestawie danych. Na przykład w przypadku filtrowania danych w tabeli zestawu danych kryteria wyszukiwania mogą zwracać różne wyniki, w zależności od tego, czy w porównaniu z rozróżnianiem wielkości liter. Ustawiając właściwość zestawu danych, można kontrolować uwzględnianie wielkości liter w filtrowaniu, wyszukiwaniu i sortowaniu <xref:System.Data.DataSet.CaseSensitive%2A> . Wszystkie tabele w zestawie danych domyślnie dziedziczą wartość tej właściwości. (Tę właściwość można zastąpić dla każdej pojedynczej tabeli, ustawiając <xref:System.Data.DataTable.CaseSensitive%2A> Właściwość tabeli).

## <a name="locate-a-specific-row-in-a-data-table"></a>Lokalizowanie określonego wiersza w tabeli danych

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Aby znaleźć wiersz w określonym zestawie danych z wartością klucza podstawowego

- Aby zlokalizować wiersz, wywołaj metodę silnie wpisaną `FindBy` , która używa klucza podstawowego tabeli.

     W poniższym przykładzie `CustomerID` kolumna jest kluczem podstawowym `Customers` tabeli. Oznacza to, że wygenerowana `FindBy` Metoda to `FindByCustomerID` . W przykładzie pokazano, jak przypisać określony element <xref:System.Data.DataRow> do zmiennej za pomocą wygenerowanej `FindBy` metody.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Aby znaleźć wiersz w nietypem DataSet z wartością klucza podstawowego

- Wywołaj <xref:System.Data.DataRowCollection.Find%2A> metodę <xref:System.Data.DataRowCollection> kolekcji, przekazując klucz podstawowy jako parametr.

     Poniższy przykład pokazuje, jak zadeklarować nowy wiersz o nazwie `foundRow` i przypisać mu wartość zwracaną <xref:System.Data.DataRowCollection.Find%2A> metody. Jeśli zostanie znaleziony klucz podstawowy, zawartość indeksu kolumn 1 zostanie wyświetlona w oknie komunikatu.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Znajdowanie wierszy według wartości kolumn

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Aby znaleźć wiersze na podstawie wartości w dowolnej kolumnie

- Tabele danych są tworzone za pomocą <xref:System.Data.DataTable.Select%2A> metody, która zwraca tablicę <xref:System.Data.DataRow> s na podstawie wyrażenia przesłanego do <xref:System.Data.DataTable.Select%2A> metody. Aby uzyskać więcej informacji na temat tworzenia prawidłowych wyrażeń, zobacz sekcję "składnia wyrażenia" na stronie o <xref:System.Data.DataColumn.Expression%2A> właściwości.

     Poniższy przykład pokazuje, jak używać <xref:System.Data.DataTable.Select%2A> metody <xref:System.Data.DataTable> do znajdowania określonych wierszy.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Dostęp do rekordów pokrewnych
Gdy tabele w zestawie danych są powiązane, <xref:System.Data.DataRelation> obiekt może udostępnić powiązane rekordy w innej tabeli. Na przykład zestaw danych zawierający `Customers` i `Orders` tabele mogą być udostępniane.

Można użyć <xref:System.Data.DataRelation> obiektu do lokalizowania powiązanych rekordów przez wywołanie <xref:System.Data.DataRow.GetChildRows%2A> metody <xref:System.Data.DataRow> w tabeli nadrzędnej. Ta metoda zwraca tablicę powiązanych rekordów podrzędnych. Lub można wywołać <xref:System.Data.DataRow.GetParentRow%2A> metodę z <xref:System.Data.DataRow> tabeli podrzędnej. Ta metoda zwraca jeden <xref:System.Data.DataRow> z tabeli nadrzędnej.

Na tej stronie przedstawiono przykłady użycia wpisanych zestawów danych. Aby uzyskać informacje na temat nawigowania po relacjach w zestawach danych, zobacz [nawigowanie po relacjach](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Jeśli pracujesz w aplikacji Windows Forms i używasz funkcji powiązania danych do wyświetlania danych, formularz wygenerowany przez projektanta może zapewnić odpowiednią funkcjonalność aplikacji. Aby uzyskać więcej informacji, zobacz [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Zapoznaj się [z tematem relacje w zestawach danych](relationships-in-datasets.md).

Poniższy przykład kodu pokazuje, jak nawigować w górę i w dół relacji w typach danych. W przykładach kodu użyto <xref:System.Data.DataRow> typu s ( `NorthwindDataSet.OrdersRow` ) i wygenerowanych metod FindBy *PrimaryKey* ( `FindByCustomerID` ), aby zlokalizować żądany wiersz i zwrócić powiązane rekordy. Przykłady kompilują i działają poprawnie tylko wtedy, gdy masz:

- Wystąpienie zestawu danych o nazwie `NorthwindDataSet` z `Customers` tabelą.

- `Orders`Tabelę.

- Relacja o nazwie odnosi `FK_Orders_Customers` się do dwóch tabel.

Ponadto obie tabele muszą być wypełnione danymi dla wszystkich rekordów, które mają zostać zwrócone.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Aby zwrócić rekordy podrzędne wybranego rekordu nadrzędnego

- Wywołaj <xref:System.Data.DataRow.GetChildRows%2A> metodę określonego `Customers` wiersza danych i zwróć tablicę wierszy z `Orders` tabeli:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Aby zwrócić rekord nadrzędny wybranego rekordu podrzędnego

- Wywołaj <xref:System.Data.DataRow.GetParentRow%2A> metodę określonego `Orders` wiersza danych i zwróć pojedynczy wiersz z `Customers` tabeli:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Zobacz też

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
