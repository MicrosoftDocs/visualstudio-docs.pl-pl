---
title: Zapisywanie danych z obiektu w bazie danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5208b7764949f6ba6d3e862c7a2102608afb7e24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648215"
---
# <a name="save-data-from-an-object-to-a-database"></a>Zapisywanie danych z obiektu w bazie danych

Dane można zapisywać w obiektach w bazie danych, przekazując wartości z obiektu do jednej z metod DBDirect TableAdapter (na przykład `TableAdapter.Insert`). Aby uzyskać więcej informacji, zobacz [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Aby zapisać dane z kolekcji obiektów, należy wykonać pętlę przez kolekcję obiektów (na przykład pętlę for-Next) i wysłać wartości dla każdego obiektu do bazy danych przy użyciu jednej z TableAdapter metod `DBDirect`.

Domyślnie metody `DBDirect` są tworzone w TableAdapter, które mogą być uruchamiane bezpośrednio w bazie danych. Metody te mogą być wywoływane bezpośrednio i nie wymagają <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> obiektów, aby uzgodnić zmiany w celu wysyłania aktualizacji do bazy danych.

> [!NOTE]
> Podczas konfigurowania TableAdapter, zapytanie główne musi dostarczyć wystarczające informacje na potrzeby tworzenia metod `DBDirect`. Na przykład jeśli TableAdapter jest skonfigurowany do wykonywania zapytań dotyczących danych z tabeli, która nie ma zdefiniowanej kolumny klucza podstawowego, nie generują `DBDirect` metod.

|TableAdapter DBDirect — Metoda|Opis|
| - |-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy do bazy danych i umożliwia przekazywanie wartości poszczególnych kolumn jako parametrów metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. Metoda `Update` przyjmuje wartości początkowe i nowe kolumny jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane do aktualizowania tego rekordu.<br /><br /> Metoda `TableAdapter.Update` służy również do uzgadniania zmian w zestawie danych z powrotem do bazy danych, pobierając <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> lub tablicę <xref:System.Data.DataRow>s jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych na podstawie wartości pierwotnej kolumny przekazaną jako parametry metody.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Aby zapisać nowe rekordy z obiektu w bazie danych

- Utwórz rekordy, przekazując wartości do metody `TableAdapter.Insert`.

     Poniższy przykład tworzy nowy rekord klienta w tabeli `Customers`, przekazując wartości w obiekcie `currentCustomer` do metody `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aby zaktualizować istniejące rekordy z obiektu do bazy danych

- Zmodyfikuj rekordy, wywołując metodę `TableAdapter.Update`, przekazując nowe wartości w celu zaktualizowania rekordu i przekazując wartości pierwotne w celu zlokalizowania rekordu.

    > [!NOTE]
    > Obiekt musi zachować oryginalne wartości, aby przekazać je do metody `Update`. W tym przykładzie do przechowywania oryginalnych wartości są stosowane właściwości z prefiksem `orig`.

     Poniższy przykład aktualizuje istniejący rekord w tabeli `Customers` przez przekazanie nowych i oryginalnych wartości w obiekcie `Customer` do metody `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Aby usunąć istniejące rekordy z bazy danych

- Usuń rekordy, wywołując metodę `TableAdapter.Delete` i przekazując wartości pierwotne w celu zlokalizowania rekordu.

    > [!NOTE]
    > Obiekt musi zachować oryginalne wartości, aby przekazać je do metody `Delete`. W tym przykładzie do przechowywania oryginalnych wartości są stosowane właściwości z prefiksem `orig`.

     Poniższy przykład usuwa rekord z tabeli `Customers` przez przekazanie oryginalnych wartości w obiekcie `Customer` do metody `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Musisz mieć uprawnienia do wykonywania wybranych `INSERT`, `UPDATE` lub `DELETE` w tabeli w bazie danych.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)