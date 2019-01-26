---
title: Edytowanie danych w zestawach danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 08cf47310c9743d1071dd46a30e5c04372ca5cb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996730"
---
# <a name="edit-data-in-datasets"></a>Edytowanie danych w zestawach danych
Możesz edytować dane w tabelach danych tak, jak edytować dane w tabeli w dowolnej bazie danych. Ten proces może zawierać Wstawianie, aktualizowanie i usuwanie rekordów w tabeli. W formie powiązanych z danymi można określić pola, które są można edytować użytkownika. W takich przypadkach infrastruktura powiązań danych obsługuje wszystkie śledzenia zmian, aby zmiany mogą zostać odesłany do bazy danych później. Jeśli programowo wprowadzisz zmiany danych, a ma zostać wysłany tych zmian w bazie danych, należy użyć obiektów i metod, które wykonują śledzenia zmian dla Ciebie.

Validated rzeczywistych danych, możesz także zbadać <xref:System.Data.DataTable> zwrócić określone wiersze danych. Na przykład może wyszukać poszczególne wiersze, określone wersje wierszy (oryginalny i proponowane), wiersze, które zostały zmienione lub wiersze, które mają błędy.

## <a name="to-edit-rows-in-a-dataset"></a>Edytowanie wierszy w zestawie danych
Aby edytować istniejący wiersz w <xref:System.Data.DataTable>, musisz zlokalizować <xref:System.Data.DataRow> chcesz edytować, a następnie przypisz zaktualizowane wartości do kolumny.

Jeśli nie znasz indeks wiersza, którą chcesz edytować, użyj `FindBy` metody, aby przeprowadzić wyszukiwanie według klucza podstawowego:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Jeśli znasz indeks wiersza, mogą uzyskiwać dostęp do i umożliwia edytowanie wierszy w następujący sposób:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Aby wstawić nowe wiersze do zestawu danych
Aplikacje, które zazwyczaj używają formantów powiązanych z danymi na dodawanie nowych rekordów za pomocą **Dodaj nowe** znajdujący się na [BindingNavigator — kontrolka](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Aby ręcznie dodać nowych rekordów do zestawu danych, należy utworzyć nowy wiersz danych przez wywołanie metody w elemencie DataTable. Następnie należy dodać wiersz, aby <xref:System.Data.DataRow> kolekcji (<xref:System.Data.DataTable.Rows%2A>) z <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Aby zachować informacje, że zestaw danych wymaga wysyłania aktualizacji do źródła danych, należy użyć <xref:System.Data.DataRow.Delete%2A> metodę, aby usunąć wiersze w tabeli danych. Na przykład, jeśli aplikacja używa TableAdapter (lub <xref:System.Data.Common.DataAdapter>), TableAdapter `Update` metoda usuwa wierszy w bazie danych, które mają <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Deleted>.

Jeśli aplikacja nie potrzebuje do wysyłania aktualizacji do źródła danych, istnieje możliwość usuwania rekordów, uzyskując bezpośrednio dostęp zbierania danych wiersza (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Do usuwania rekordów z tabeli danych

-   Wywołaj <xref:System.Data.DataRow.Delete%2A> metody <xref:System.Data.DataRow>.

     Ta metoda nie usuwa fizycznie rekordu. Zamiast tego oznacza rekord do usunięcia.

    > [!NOTE]
    >  Jeśli liczba własności <xref:System.Data.DataRowCollection>, wynikowa liczba zawiera rekordy, które zostały oznaczone do usunięcia. Aby uzyskać dokładne liczba rekordów, które nie są oznaczone do usunięcia, można pętli kolekcji patrząc <xref:System.Data.DataRow.RowState%2A> właściwości każdego rekordu. (Rekordy oznaczone do usunięcia mają <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Deleted>.) Można utworzyć widok danych zestawu danych, który filtry oparte na stanie wiersza i pobieranie właściwości z tego miejsca.

Poniższy przykład pokazuje sposób wywoływania <xref:System.Data.DataRow.Delete%2A> metodę, aby oznaczyć pierwszy wiersz `Customers` tabeli jako usunięty:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Określić, czy istnieją zmienione wiersze
Gdy zostaną wprowadzone zmiany do rekordów w zestawie danych, informacje o tych zmianach są przechowywane aż je zatwierdzisz. Zatwierdź zmiany po wywołaniu `AcceptChanges` metody tabeli danych lub zestaw danych lub po wywołaniu `Update` metody TableAdapter lub danych adaptera.

Zmiany są śledzone dwa sposoby, w każdym wierszu danych:

-   Każdy wiersz danych zawiera informacje dotyczące jego <xref:System.Data.DataRow.RowState%2A> (na przykład <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, lub <xref:System.Data.DataRowState.Unchanged>).

-   Każdy zmieniony wiersz danych zawiera wiele wersji tego wiersza (<xref:System.Data.DataRowVersion>), wersja oryginalna (przed zmianami) i bieżącej wersji (po zmianach). W okresie, gdy zmiany oczekujące (czas, kiedy, pozwalające reagować na <xref:System.Data.DataTable.RowChanging> zdarzeń), trzecia wersja — wersja proponowana — jest także dostępna.

<xref:System.Data.DataSet.HasChanges%2A> Metoda zestawu danych zwraca `true` Jeśli wprowadzono zmiany w zestawie danych. Po ustaleniu, że istnieją zmienione wiersze, można wywołać `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> zwrócić zestaw zmienionych wierszy.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Aby ustalić, czy wprowadzono zmiany do wszystkich wierszy

-   Wywołaj <xref:System.Data.DataSet.HasChanges%2A> metoda zestawu danych, aby sprawdzić zmienione wiersze.

Poniższy przykład pokazuje, jak sprawdzić wartość zwrotną z elementu <xref:System.Data.DataSet.HasChanges%2A> metody wykrywania, czy istnieją jakiekolwiek zmienione wiersze w zestawie danych o nazwie `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Określanie typu zmian
Możesz również sprawdzić, aby zobaczyć, jaki typ zmiany wprowadzono w zestawie danych, przekazując wartość z zakresu od <xref:System.Data.DataRowState> wyliczeniu, aby <xref:System.Data.DataSet.HasChanges%2A> metody.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Aby określić, jakie zmiany zostały wprowadzone, aby wiersz

-   Przekaż <xref:System.Data.DataRowState> wartość <xref:System.Data.DataSet.HasChanges%2A> metody.

Poniższy przykład pokazuje, jak sprawdzić zestaw danych o nazwie `NorthwindDataset1` ustalenie, jeśli jakieś nowe wiersze zostały dodane do niego:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Aby zlokalizować wierszy zawierających błędy
Podczas pracy z poszczególnych kolumn i wierszy danych, mogą wystąpić błędy. Możesz sprawdzić `HasErrors` właściwości w celu określenia, jeśli istnieją błędy w <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow>.

1.  Sprawdź `HasErrors` właściwości, aby zobaczyć, czy istnieją błędy w zestawie danych.

2.  Jeśli `HasErrors` właściwość `true`, iterowania przez kolekcje tabel, a następnie za pomocą wierszy, aby znaleźć wiersza z powodu błędu.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)