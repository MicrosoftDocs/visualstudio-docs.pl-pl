---
title: Edytowanie danych w zestawach danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65e01b13fb1bec83cc7254133c99c16a98220e22
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648834"
---
# <a name="edit-data-in-datasets"></a>Edytowanie danych w zestawach danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Możesz edytować dane w tabelach danych tak, jak edytować dane w tabeli w dowolnej bazie danych. Ten proces może zawierać Wstawianie, aktualizowanie i usuwanie rekordów w tabeli. W formie powiązanych z danymi można określić pola, które są można edytować użytkownika. W takich przypadkach infrastruktura powiązań danych obsługuje wszystkie śledzenia zmian, aby zmiany mogą zostać odesłany do bazy danych później. Jeśli programowo wprowadzisz zmiany danych, a ma zostać wysłany tych zmian w bazie danych, należy użyć obiektów i metod, które wykonują śledzenia zmian dla Ciebie.  
  
 Validated rzeczywistych danych, możesz także zbadać <xref:System.Data.DataTable> zwrócić określone wiersze danych. Na przykład może wyszukać poszczególne wiersze, określone wersje wierszy (oryginalny i proponowane), wiersze, które zostały zmienione lub wiersze, które mają błędy.  
  
## <a name="to-edit-rows-in-a-dataset"></a>Edytowanie wierszy w zestawie danych  
 Aby edytować istniejący wiersz w <xref:System.Data.DataTable>, musisz zlokalizować <xref:System.Data.DataRow> chcesz edytować, a następnie przypisz zaktualizowane wartości do kolumny.  
  
 Jeśli nie znasz indeks wiersza, którą chcesz edytować, użyj `FindBy` metody, aby przeprowadzić wyszukiwanie według klucza podstawowego:  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 Jeśli znasz indeks wiersza, mogą uzyskiwać dostęp do i umożliwia edytowanie wierszy w następujący sposób:  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>Aby wstawić nowe wiersze do zestawu danych  
 Aplikacje, które zazwyczaj używają formantów powiązanych z danymi na dodawanie nowych rekordów za pomocą **Dodaj nowe** znajdujący się na [BindingNavigator — kontrolka](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
 Aby ręcznie dodać nowych rekordów do zestawu danych, należy utworzyć nowy wiersz danych przez wywołanie metody w elemencie DataTable. Następnie dodaj wiersz, aby <xref:System.Data.DataRow> kolekcji (<xref:System.Data.DataTable.Rows%2A>) z <xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 Aby zachować informacje, że zestaw danych wymaga wysyłania aktualizacji do źródła danych, należy użyć <xref:System.Data.DataRow.Delete%2A> metodę, aby usunąć wiersze w tabeli danych. Na przykład, jeśli aplikacja używa TableAdapter (lub <xref:System.Data.Common.DataAdapter>), TableAdapter `Update` metoda usuwa wierszy w bazie danych, które mają <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState>.  
  
 Jeśli aplikacja nie potrzebuje do wysyłania aktualizacji do źródła danych, to można usunąć rekordów, uzyskując bezpośrednio dostęp do kolekcji wierszy danych (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>Do usuwania rekordów z tabeli danych  
  
-   Wywołaj <xref:System.Data.DataRow.Delete%2A> metody <xref:System.Data.DataRow>.  
  
     Ta metoda nie usuwa fizycznie rekordu. Zamiast tego oznacza rekord do usunięcia.  
  
    > [!NOTE]
    >  Jeśli liczba własności <xref:System.Data.DataRowCollection>, wynikowa liczba zawiera rekordy, które zostały oznaczone do usunięcia. Aby uzyskać dokładne liczba rekordów, które nie są oznaczone do usunięcia, można pętli kolekcji patrząc <xref:System.Data.DataRow.RowState%2A> właściwości każdego rekordu. (Rekordy oznaczone do usunięcia mają <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState>.) Można utworzyć widok danych zestawu danych, który filtry oparte na stanie wiersza i pobieranie właściwości z tego miejsca.  
  
     Poniższy przykład pokazuje sposób wywoływania <xref:System.Data.DataRow.Delete%2A> metodę, aby oznaczyć pierwszy wiersz `Customers` tabeli jako usunięty:  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Określić, czy istnieją zmienione wiersze  
 Gdy zostaną wprowadzone zmiany do rekordów w zestawie danych, informacje o tych zmianach są przechowywane aż je zatwierdzisz. Zatwierdź zmiany po wywołaniu `AcceptChanges` metody tabeli danych lub zestaw danych lub po wywołaniu `Update` metody TableAdapter lub danych adaptera.  
  
 Zmiany są śledzone dwa sposoby, w każdym wierszu danych:  
  
- Każdy wiersz danych zawiera informacje powiązane z jego <xref:System.Data.DataRow.RowState%2A> (na przykład <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, lub <xref:System.Data.DataRowState>).  
  
- Każdy zmieniony wiersz danych zawiera wiele wersji tego wiersza (<xref:System.Data.DataRowVersion>), wersja oryginalna (przed zmianami) i bieżącej wersji (po zmianach). W okresie, gdy zmiany oczekujące (czas, kiedy, pozwalające reagować na <xref:System.Data.DataTable.RowChanging> zdarzeń), trzecia wersja — wersja proponowana — jest także dostępna.
  
  <xref:System.Data.DataSet.HasChanges%2A> Metoda zestawu danych zwraca `true` Jeśli wprowadzono zmiany w zestawie danych. Po ustaleniu, że istnieją zmienione wiersze, można wywołać `GetChanges` metody <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> zwrócić zestaw zmienionych wierszy. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie zmienionych wierszy](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Aby ustalić, czy wprowadzono zmiany do wszystkich wierszy  
  
-   Wywołaj <xref:System.Data.DataSet.HasChanges%2A> metoda zestawu danych, aby sprawdzić zmienione wiersze.  
  
     Poniższy przykład pokazuje, jak sprawdzić wartość zwrotną z elementu <xref:System.Data.DataSet.HasChanges%2A> metody wykrywania, czy istnieją jakiekolwiek zmienione wiersze w zestawie danych o nazwie `NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>Określanie typu zmian  
 Możesz również sprawdzić, aby zobaczyć, jaki typ zmiany wprowadzono w zestawie danych, przekazując wartość z zakresu od <xref:System.Data.DataRowState> wyliczeniu, aby <xref:System.Data.DataSet.HasChanges%2A> metody.  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Aby określić, jakie zmiany zostały wprowadzone, aby wiersz  
  
-   Przekaż <xref:System.Data.DataRowState> wartość <xref:System.Data.DataSet.HasChanges%2A> metody.  
  
     Poniższy przykład pokazuje, jak sprawdzić zestaw danych o nazwie `NorthwindDataset1` ustalenie, jeśli jakieś nowe wiersze zostały dodane do niego:  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>Aby zlokalizować wierszy zawierających błędy  
 Podczas pracy z poszczególnych kolumn i wierszy danych, mogą wystąpić błędy. Możesz sprawdzić `HasErrors` właściwości w celu określenia, jeśli istnieją błędy w <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow>.  
  
1.  Sprawdź `HasErrors` właściwości, aby zobaczyć, czy istnieją błędy w zestawie danych.  
  
2.  Jeśli `HasErrors` właściwość `true`, iterowania przez kolekcje tabel, a następnie za pomocą wierszy, aby znaleźć wiersza z powodu błędu.  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
