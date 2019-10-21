---
title: Zapisywanie danych z obiektu w bazie danych | Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607454"
---
# <a name="save-data-from-an-object-to-a-database"></a>Zapisywanie danych z obiektu w bazie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dane można zapisywać w obiektach w bazie danych, przekazując wartości z obiektu do jednej z metod DBDirect TableAdapter (na przykład `TableAdapter.Insert`).

 Aby zapisać dane z kolekcji obiektów, należy wykonać pętlę przez kolekcję obiektów (na przykład pętlę for-Next) i wysłać wartości dla każdego obiektu do bazy danych przy użyciu jednej z metod DBDirect TableAdapter.

 Domyślnie metody DBDirect są tworzone w TableAdapter, które mogą być uruchamiane bezpośrednio w bazie danych. Metody te mogą być wywoływane bezpośrednio i nie wymagają <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> obiektów, aby uzgodnić zmiany w celu wysyłania aktualizacji do bazy danych.

> [!NOTE]
> Gdy konfigurujesz TableAdapter, główne zapytanie musi dostarczyć wystarczające informacje dla metod DBDirect, które mają zostać utworzone. Na przykład, jeśli TableAdapter jest skonfigurowany do wykonywania zapytań dotyczących danych z tabeli, która nie ma zdefiniowanej kolumny klucza podstawowego, nie generują metod DBDirect.

|TableAdapter DBDirect — Metoda|Opis|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy do bazy danych i umożliwia przekazywanie wartości poszczególnych kolumn jako parametrów metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. Metoda `Update` przyjmuje wartości początkowe i nowe kolumny jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane do aktualizowania tego rekordu.<br /><br /> Metoda `TableAdapter.Update` służy również do uzgadniania zmian w zestawie danych z powrotem do bazy danych, pobierając <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> lub tablicę <xref:System.Data.DataRow>s jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych na podstawie wartości pierwotnej kolumny przekazaną jako parametry metody.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Aby zapisać nowe rekordy z obiektu w bazie danych

- Utwórz rekordy, przekazując wartości do metody `TableAdapter.Insert`.

     Poniższy przykład tworzy nowy rekord klienta w tabeli `Customers`, przekazując wartości w obiekcie `currentCustomer` do metody `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aby zaktualizować istniejące rekordy z obiektu do bazy danych

- Zmodyfikuj rekordy, wywołując metodę `TableAdapter.Update`, przekazując nowe wartości w celu zaktualizowania rekordu i przekazując wartości pierwotne w celu zlokalizowania rekordu.

    > [!NOTE]
    > Obiekt musi zachować oryginalne wartości, aby przekazać je do metody `Update`. W tym przykładzie do przechowywania oryginalnych wartości są stosowane właściwości z prefiksem `orig`.

     Poniższy przykład aktualizuje istniejący rekord w tabeli `Customers` przez przekazanie nowych i oryginalnych wartości w obiekcie `Customer` do metody `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Aby usunąć istniejące rekordy z bazy danych

- Usuń rekordy, wywołując metodę `TableAdapter.Delete` i przekazując wartości pierwotne w celu zlokalizowania rekordu.

    > [!NOTE]
    > Obiekt musi zachować oryginalne wartości, aby przekazać je do metody `Delete`. W tym przykładzie do przechowywania oryginalnych wartości są stosowane właściwości z prefiksem `orig`.

     Poniższy przykład usuwa rekord z tabeli `Customers` przez przekazanie oryginalnych wartości w obiekcie `Customer` do metody `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework
 Musisz mieć uprawnienia do wykonywania wybranych instrukcji INSERT, UPDATE lub DELETE w tabeli w bazie danych.

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
