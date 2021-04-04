---
title: Zapisywanie danych z obiektu w bazie danych
description: Zapisz dane z obiektu w bazie danych przy użyciu narzędzi zestawu danych w programie Visual Studio. Zobacz, jak zapisywać nowe rekordy, aktualizować istniejące rekordy i usuwać istniejące rekordy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 50debf24fa691ba74d082543b1c0bb1a27b5786e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215789"
---
# <a name="save-data-from-an-object-to-a-database"></a>Zapisywanie danych z obiektu w bazie danych

Dane można zapisywać w obiektach w bazie danych, przekazując wartości z obiektu do jednej z metod DBDirect TableAdapter (na przykład `TableAdapter.Insert` ). Aby uzyskać więcej informacji, zobacz [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Aby zapisać dane z kolekcji obiektów, należy wykonać pętlę przez kolekcję obiektów (na przykład pętlę for-Next) i wysłać wartości dla każdego obiektu do bazy danych przy użyciu jednej z `DBDirect` metod TableAdapter.

Domyślnie `DBDirect` metody są tworzone na TableAdapter, który można uruchomić bezpośrednio w bazie danych. Metody te mogą być wywoływane bezpośrednio i nie wymagają <xref:System.Data.DataSet> ani <xref:System.Data.DataTable> obiektów do uzgadniania zmian w celu wysyłania aktualizacji do bazy danych.

> [!NOTE]
> Podczas konfigurowania TableAdapter, główne zapytanie musi zawierać wystarczające informacje dla `DBDirect` metod, które mają zostać utworzone. Na przykład, jeśli TableAdapter jest skonfigurowany do wykonywania zapytań dotyczących danych z tabeli, która nie ma zdefiniowanej kolumny klucza podstawowego, nie generują one `DBDirect` metod.

|TableAdapter DBDirect — Metoda|Opis|
| - |-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy do bazy danych i umożliwia przekazywanie wartości poszczególnych kolumn jako parametrów metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. `Update`Metoda przyjmuje wartości pierwotne i nowe kolumny jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane do aktualizowania tego rekordu.<br /><br /> `TableAdapter.Update`Metoda jest również używana do uzgadniania zmian w zestawie danych z powrotem do bazy danych przez pobranie <xref:System.Data.DataSet> ,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> lub tablicę <xref:System.Data.DataRow> s jako parametrów metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych na podstawie wartości pierwotnej kolumny przekazaną jako parametry metody.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Aby zapisać nowe rekordy z obiektu w bazie danych

- Utwórz rekordy, przekazując wartości do `TableAdapter.Insert` metody.

     Poniższy przykład tworzy nowy rekord klienta w `Customers` tabeli, przekazując wartości w `currentCustomer` obiekcie do `TableAdapter.Insert` metody.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aby zaktualizować istniejące rekordy z obiektu do bazy danych

- Zmodyfikuj rekordy, wywołując `TableAdapter.Update` metodę, przekazując nowe wartości w celu zaktualizowania rekordu i przekazując wartości pierwotne w celu zlokalizowania rekordu.

    > [!NOTE]
    > Obiekt musi zachować oryginalne wartości, aby przekazać je do `Update` metody. W tym przykładzie zastosowano właściwości z `orig` prefiksem do przechowywania oryginalnych wartości.

     Poniższy przykład aktualizuje istniejący rekord w `Customers` tabeli, przekazując nowe i oryginalne wartości w `Customer` obiekcie do `TableAdapter.Update` metody.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet24":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet24":::

## <a name="to-delete-existing-records-from-a-database"></a>Aby usunąć istniejące rekordy z bazy danych

- Usuń rekordy, wywołując `TableAdapter.Delete` metodę i przekazując wartości pierwotne w celu zlokalizowania rekordu.

    > [!NOTE]
    > Obiekt musi zachować oryginalne wartości, aby przekazać je do `Delete` metody. W tym przykładzie zastosowano właściwości z `orig` prefiksem do przechowywania oryginalnych wartości.

     Poniższy przykład usuwa rekord z `Customers` tabeli przez przekazanie oryginalnych wartości w `Customer` obiekcie do `TableAdapter.Delete` metody.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet25":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet25":::

## <a name="net-security"></a>Zabezpieczenia platformy .NET

Musisz mieć uprawnienia do wykonywania wybranych `INSERT` `UPDATE` lub `DELETE` w tabeli w bazie danych.

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
