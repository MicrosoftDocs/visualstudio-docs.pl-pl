---
title: Edytuj dane w zestawach danych | Microsoft Docs
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672401"
---
# <a name="edit-data-in-datasets"></a>Edytowanie danych w zestawach danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dane można edytować w tabelach danych tak samo, jak w przypadku edytowania danych w tabeli w dowolnej bazie danych. Proces ten może obejmować Wstawianie, aktualizowanie i usuwanie rekordów w tabeli. W formularzu związanym z danymi można określić, które pola są edytowane przez użytkownika. W takich przypadkach infrastruktura powiązań danych obsługuje wszystkie śledzenia zmian, dzięki czemu zmiany mogą być wysyłane z powrotem do bazy danych później. Jeśli programowo wprowadzisz zmiany do danych i zamierzasz wysłać je z powrotem do bazy danych, musisz użyć obiektów i metod, które umożliwiają śledzenie zmian.

 Oprócz zmiany rzeczywistych danych, można również wykonać zapytania a w <xref:System.Data.DataTable> celu zwrócenia określonych wierszy danych. Można na przykład wykonywać zapytania dotyczące pojedynczych wierszy, określonych wersji wierszy (oryginał i proponowane), wierszy, które uległy zmianie, lub wierszy z błędami.

## <a name="to-edit-rows-in-a-dataset"></a>Aby edytować wiersze w zestawie danych
 Aby edytować istniejący wiersz w, należy <xref:System.Data.DataTable> zlokalizować <xref:System.Data.DataRow> , który chcesz edytować, a następnie przypisać zaktualizowane wartości do żądanych kolumn.

 Jeśli nie znasz indeksu wiersza, który chcesz edytować, użyj `FindBy` metody, aby wyszukać według klucza podstawowego:

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Jeśli znasz indeks wierszy, możesz uzyskać dostęp do wierszy i edytować je w następujący sposób:

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Aby wstawić nowe wiersze do zestawu danych
 Aplikacje korzystające z formantów powiązanych z danymi zwykle dodają nowe rekordy za pomocą przycisku **Dodaj nowy** w [kontrolce BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

 Aby ręcznie dodać nowe rekordy do zestawu danych, Utwórz nowy wiersz danych przez wywołanie metody w elemencie DataTable. Następnie Dodaj wiersz do <xref:System.Data.DataRow> kolekcji ( <xref:System.Data.DataTable.Rows%2A> ) <xref:System.Data.DataTable> :

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Aby zachować informacje wymagane przez zestaw danych do wysyłania aktualizacji do źródła danych, należy użyć <xref:System.Data.DataRow.Delete%2A> metody usuwania wierszy w tabeli danych. Na przykład jeśli aplikacja używa elementu TableAdapter (lub <xref:System.Data.Common.DataAdapter> ), `Update` Metoda TableAdapter usuwa wiersze z bazy danych, która ma <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState> .

 Jeśli aplikacja nie musi wysyłać aktualizacji z powrotem do źródła danych, można usunąć rekordy, uzyskując bezpośrednio dostęp do kolekcji wierszy danych ( <xref:System.Data.DataRowCollection.Remove%2A> ).

#### <a name="to-delete-records-from-a-data-table"></a>Aby usunąć rekordy z tabeli danych

- Wywołaj <xref:System.Data.DataRow.Delete%2A> metodę <xref:System.Data.DataRow> .

     Ta metoda nie usuwa fizycznie rekordu. Zamiast tego oznacza rekord do usunięcia.

    > [!NOTE]
    > Jeśli otrzymasz Właściwość Count obiektu <xref:System.Data.DataRowCollection> , wynikowa liczba zawiera rekordy, które zostały oznaczone do usunięcia. Aby uzyskać dokładną liczbę rekordów, które nie są oznaczone do usunięcia, można wykonać pętlę w kolekcji, przeglądając <xref:System.Data.DataRow.RowState%2A> Właściwość każdego rekordu. (Rekordy oznaczone do usunięcia mają wartość <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState> ). Alternatywnie możesz utworzyć widok danych dla zestawu danych, który filtruje na podstawie stanu wiersza i pobrać z niego Właściwość Count.

     Poniższy przykład pokazuje, jak wywołać metodę, <xref:System.Data.DataRow.Delete%2A> Aby oznaczyć pierwszy wiersz w `Customers` tabeli jako usunięty:

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Ustal, czy zostały zmienione wiersze
 Gdy zmiany są wprowadzane do rekordów w zestawie danych, informacje o tych zmianach są przechowywane do momentu ich zatwierdzenia. Zmiany są zatwierdzane po wywołaniu `AcceptChanges` metody zestawu danych lub tabeli danych albo wywołaniu `Update` metody TableAdapter lub adaptera danych.

 Zmiany są śledzone dwa sposoby w każdym wierszu danych:

- Każdy wiersz danych zawiera informacje powiązane z tym <xref:System.Data.DataRow.RowState%2A> (na przykład,, <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> lub <xref:System.Data.DataRowState> ).

- Każdy zmieniony wiersz danych zawiera wiele wersji tego wiersza ( <xref:System.Data.DataRowVersion> ), oryginalną wersję (przed zmianami) i bieżącą wersję (po zmianach). W okresie oczekiwania na zmianę (czas reakcji na <xref:System.Data.DataTable.RowChanging> zdarzenie), trzecia wersja — proponowana wersja — jest również dostępna.

  <xref:System.Data.DataSet.HasChanges%2A>Metoda zestawu danych zwraca, `true` Jeśli wprowadzono zmiany w zestawie danych. Po ustaleniu, że istnieją zmienione wiersze, można wywołać `GetChanges` metodę lub, <xref:System.Data.DataSet> <xref:System.Data.DataTable> Aby zwrócić zestaw zmienionych wierszy. Aby uzyskać więcej informacji, zobacz [How to: pobieranie zmienionych wierszy](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Aby określić, czy wprowadzono zmiany w dowolnych wierszach

- Wywołaj <xref:System.Data.DataSet.HasChanges%2A> metodę zestawu danych, aby sprawdzić, czy zmieniono wiersze.

     Poniższy przykład pokazuje, jak sprawdzić wartość zwracaną z metody, <xref:System.Data.DataSet.HasChanges%2A> Aby wykryć, czy istnieją jakiekolwiek zmienione wiersze w zestawie danych o nazwie `NorthwindDataset1` :

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Określanie typu zmian
 Możesz również sprawdzić, czy typ zmian został wprowadzony w zestawie danych, przekazując wartość z <xref:System.Data.DataRowState> wyliczenia do <xref:System.Data.DataSet.HasChanges%2A> metody.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Aby określić, jakiego typu zmiany zostały dokonane w wierszu

- Przekaż <xref:System.Data.DataRowState> wartość do <xref:System.Data.DataSet.HasChanges%2A> metody.

     Poniższy przykład pokazuje, jak sprawdzić zestaw danych o nazwie `NorthwindDataset1` , aby określić, czy dodano do niego nowe wiersze:

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Aby zlokalizować wiersze z błędami
 Podczas pracy z poszczególnymi kolumnami i wierszami danych mogą wystąpić błędy. Możesz sprawdzić `HasErrors` Właściwość, aby określić, czy błędy istnieją w <xref:System.Data.DataSet> , <xref:System.Data.DataTable> , czy <xref:System.Data.DataRow> .

1. Sprawdź `HasErrors` Właściwość, aby sprawdzić, czy w zestawie danych występują błędy.

2. Jeśli `HasErrors` Właściwość jest `true` , wykonaj iterację kolekcji tabel, a następnie za pomocą wierszy, aby znaleźć wiersz z błędem.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
