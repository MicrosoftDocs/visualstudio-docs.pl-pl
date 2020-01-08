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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b51b5b4be12f76e2237ff93659617e1c1843722a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586656"
---
# <a name="edit-data-in-datasets"></a>Edytowanie danych w zestawach danych
Dane można edytować w tabelach danych tak samo, jak w przypadku edytowania danych w tabeli w dowolnej bazie danych. Proces ten może obejmować Wstawianie, aktualizowanie i usuwanie rekordów w tabeli. W formularzu związanym z danymi można określić, które pola są edytowane przez użytkownika. W takich przypadkach infrastruktura powiązań danych obsługuje wszystkie śledzenia zmian, dzięki czemu zmiany mogą być wysyłane z powrotem do bazy danych później. Jeśli programowo wprowadzisz zmiany do danych i zamierzasz wysłać je z powrotem do bazy danych, musisz użyć obiektów i metod, które umożliwiają śledzenie zmian.

Oprócz zmiany rzeczywistych danych można również wysyłać zapytania do <xref:System.Data.DataTable>, aby zwrócić określone wiersze danych. Można na przykład wykonywać zapytania dotyczące pojedynczych wierszy, określonych wersji wierszy (oryginał i proponowane), wierszy, które uległy zmianie, lub wierszy z błędami.

## <a name="to-edit-rows-in-a-dataset"></a>Aby edytować wiersze w zestawie danych
Aby edytować istniejący wiersz w <xref:System.Data.DataTable>, należy zlokalizować <xref:System.Data.DataRow>, które chcesz edytować, a następnie przypisać zaktualizowane wartości do żądanych kolumn.

Jeśli nie znasz indeksu wiersza, który chcesz edytować, użyj metody `FindBy`, aby wyszukać według klucza podstawowego:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Jeśli znasz indeks wierszy, możesz uzyskać dostęp do wierszy i edytować je w następujący sposób:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Aby wstawić nowe wiersze do zestawu danych
Aplikacje korzystające z formantów powiązanych z danymi zwykle dodają nowe rekordy za pomocą przycisku **Dodaj nowy** w [kontrolce BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Aby ręcznie dodać nowe rekordy do zestawu danych, Utwórz nowy wiersz danych przez wywołanie metody w elemencie DataTable. Następnie Dodaj wiersz do kolekcji <xref:System.Data.DataRow> (<xref:System.Data.DataTable.Rows%2A>) <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Aby zachować informacje wymagane przez zestaw danych do wysyłania aktualizacji do źródła danych, należy użyć metody <xref:System.Data.DataRow.Delete%2A>, aby usunąć wiersze w tabeli danych. Na przykład, jeśli aplikacja korzysta z TableAdapter (lub <xref:System.Data.Common.DataAdapter>), Metoda `Update`a TableAdapter usuwa z bazy danych wiersze, które mają <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted>.

Jeśli aplikacja nie musi wysyłać aktualizacji z powrotem do źródła danych, można usunąć rekordy, bezpośrednio uzyskując dostęp do kolekcji wierszy danych (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Aby usunąć rekordy z tabeli danych

- Wywołaj metodę <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow>.

     Ta metoda nie usuwa fizycznie rekordu. Zamiast tego oznacza rekord do usunięcia.

    > [!NOTE]
    > Jeśli otrzymasz Właściwość Count <xref:System.Data.DataRowCollection>, wynikowa liczba zawiera rekordy, które zostały oznaczone do usunięcia. Aby uzyskać dokładną liczbę rekordów, które nie są oznaczone do usunięcia, można wykonać pętlę w kolekcji, przeglądając Właściwość <xref:System.Data.DataRow.RowState%2A> każdego rekordu. (Rekordy oznaczone do usunięcia mają <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted>.) Alternatywnie możesz utworzyć widok danych dla zestawu danych, który filtruje na podstawie stanu wiersza i pobrać z niego Właściwość Count.

Poniższy przykład pokazuje, jak wywołać metodę <xref:System.Data.DataRow.Delete%2A>, aby oznaczyć pierwszy wiersz w tabeli `Customers` jako usunięty:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Ustal, czy zostały zmienione wiersze
Gdy zmiany są wprowadzane do rekordów w zestawie danych, informacje o tych zmianach są przechowywane do momentu ich zatwierdzenia. Zmiany są zatwierdzane po wywołaniu metody `AcceptChanges` zestawu danych lub tabeli danych lub wywołaniu metody `Update` karty TableAdapter lub adaptera danych.

Zmiany są śledzone dwa sposoby w każdym wierszu danych:

- Każdy wiersz danych zawiera informacje dotyczące <xref:System.Data.DataRow.RowState%2A> (na przykład <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>lub <xref:System.Data.DataRowState.Unchanged>).

- Każdy zmieniony wiersz danych zawiera wiele wersji tego wiersza (<xref:System.Data.DataRowVersion>), oryginalną wersję (przed zmianami) i bieżącą wersję (po zmianach). W czasie oczekiwania na zmianę (czas, w którym można odpowiedzieć na zdarzenie <xref:System.Data.DataTable.RowChanging>), trzecia wersja — proponowana wersja — jest również dostępna.

Metoda <xref:System.Data.DataSet.HasChanges%2A> zestawu danych zwraca `true`, jeśli wprowadzono zmiany w zestawie danych. Po ustaleniu, że istnieją zmienione wiersze, można wywołać metodę `GetChanges` <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>, aby zwrócić zestaw zmienionych wierszy.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Aby określić, czy wprowadzono zmiany w dowolnych wierszach

- Wywołaj metodę <xref:System.Data.DataSet.HasChanges%2A> zestawu danych, aby sprawdzić, czy zmieniono wiersze.

Poniższy przykład pokazuje, jak sprawdzić wartość zwracaną z metody <xref:System.Data.DataSet.HasChanges%2A>, aby wykryć, czy istnieją jakiekolwiek zmienione wiersze w zestawie danych o nazwie `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Określanie typu zmian
Możesz również sprawdzić, czy typ zmian został wprowadzony w zestawie danych, przekazując wartość z wyliczenia <xref:System.Data.DataRowState> do metody <xref:System.Data.DataSet.HasChanges%2A>.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Aby określić, jakiego typu zmiany zostały dokonane w wierszu

- Przekaż <xref:System.Data.DataRowState> wartość do metody <xref:System.Data.DataSet.HasChanges%2A>.

Poniższy przykład pokazuje, jak sprawdzić zestaw danych o nazwie `NorthwindDataset1`, aby określić, czy dodano do niego nowe wiersze:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Aby zlokalizować wiersze z błędami
Podczas pracy z poszczególnymi kolumnami i wierszami danych mogą wystąpić błędy. Możesz sprawdzić Właściwość `HasErrors`, aby określić, czy błędy istnieją w <xref:System.Data.DataSet>, <xref:System.Data.DataTable>lub <xref:System.Data.DataRow>.

1. Sprawdź Właściwość `HasErrors`, aby sprawdzić, czy w zestawie danych występują błędy.

2. Jeśli właściwość `HasErrors` jest `true`, wykonaj iterację kolekcji tabel, a następnie za pomocą wierszy, aby znaleźć wiersz z błędem.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Zobacz także

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
