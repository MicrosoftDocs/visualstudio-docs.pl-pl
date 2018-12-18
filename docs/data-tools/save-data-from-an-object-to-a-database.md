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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1203b3b129b42ca65b94cd7a4b9cebf108740f4
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750953"
---
# <a name="save-data-from-an-object-to-a-database"></a>Zapisywanie danych z obiektu w bazie danych

Można zapisać danych w obiektach do bazy danych przez przekazanie wartości z obiektu do jednej z TableAdapter dbdirect — metody (na przykład `TableAdapter.Insert`). Aby uzyskać więcej informacji, zobacz [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Aby zapisać dane z kolekcji obiektów, w pętli poprzez kolekcji obiektów (na przykład pętli for dalej) i wysyłać wartości dla każdego obiektu bazy danych przy użyciu jednej z TableAdapter `DBDirect` metody.

Domyślnie `DBDirect` metody są tworzone na obiekt TableAdapter, który można uruchomić bezpośrednio w bazie danych. Te metody może być wywoływana bezpośrednio i nie wymagają <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> obiektów uzgadniają zmiany w celu wysyłania aktualizacji do bazy danych.

> [!NOTE]
> Podczas konfiguracji TableAdapter główne zapytanie musi dostarczać wystarczających informacji dla `DBDirect` metod, które ma zostać utworzony. Na przykład, jeśli TableAdapter jest skonfigurowany do zapytania o dane z tabeli, która nie ma kolumny klucza podstawowego zdefiniowane, nie generuje ona `DBDirect` metody.

|TableAdapter dbdirect — metody|Opis|
| - |-----------------|
|`TableAdapter.Insert`|Dodanie nowych rekordów do bazy danych i umożliwia przekazywanie wartości poszczególnych kolumn jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. `Update` Metoda przyjmuje wartości oryginalnego i nowych kolumn jako parametry metody. Oryginalne wartości są używane do lokalizowania oryginalnego rekordu, a nowe wartości są używane na zaktualizowanie rekordu.<br /><br /> `TableAdapter.Update` Metoda umożliwia również uzgadniają zmiany w zestawie danych w bazie danych, wykonując <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, lub tablicę <xref:System.Data.DataRow>określane jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych oparte na oryginalnych wartości kolumny przekazanych jako parametry metody.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Aby zapisać nowe rekordy z obiektu do bazy danych

-   Tworzenie rekordów przez przekazanie wartości do `TableAdapter.Insert` metody.

     Poniższy przykład tworzy nowy rekord klienta `Customers` tabeli przez przekazanie wartości w `currentCustomer` obiekt `TableAdapter.Insert` metody.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aby zaktualizować istniejące rekordy z obiektu do bazy danych

-   Modyfikowanie rekordów, wywołując `TableAdapter.Update` metody, przekazując nowe wartości w celu zaktualizowania rekordu, a w oryginalnych wartości, aby zlokalizować rekordu.

    > [!NOTE]
    > Trzeba zachować oryginalne wartości, aby można było przekazać je do obiektu `Update` metody. W tym przykładzie użyto właściwości `orig` prefiks do przechowywania oryginalnych wartości.

     Poniższy przykład aktualizuje istniejący rekord w `Customers` tabeli przez przekazanie wartości nowymi i oryginalnymi `Customer` obiekt `TableAdapter.Update` metody.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Aby usunąć istniejące rekordy z bazy danych

-   Usuń rekordy przez wywołanie metody `TableAdapter.Delete` metody i przekazywanie w oryginalnej wartości do wyszukania w rekordzie.

    > [!NOTE]
    > Trzeba zachować oryginalne wartości, aby można było przekazać je do obiektu `Delete` metody. W tym przykładzie użyto właściwości `orig` prefiks do przechowywania oryginalnych wartości.

     Poniższy przykład usuwa rekord na podstawie `Customers` tabeli, przekazując oryginalnych wartości w `Customer` obiekt `TableAdapter.Delete` metody.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Musi mieć uprawnienia do wykonania wybranej `INSERT`, `UPDATE`, lub `DELETE` w tabeli w bazie danych.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)