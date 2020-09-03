---
title: Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 22d84e9b4beafd64cc629a295bcfa7f9f67afb6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282569"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter

Oprócz `InsertCommand` , `UpdateCommand` , i `DeleteCommand` , TableAdapters są tworzone przy użyciu metod, które mogą być uruchamiane bezpośrednio w bazie danych. Można wywołać te metody ( `TableAdapter.Insert` , `TableAdapter.Update` i `TableAdapter.Delete` ) do manipulowania danymi bezpośrednio w bazie danych.

Jeśli nie chcesz tworzyć tych metod bezpośrednich, ustaw `GenerateDbDirectMethods` Właściwość TableAdapter `false` w oknie **Właściwości** . Jeśli jakiekolwiek zapytania są dodawane do elementu TableAdapter oprócz głównego zapytania TableAdapter, są to zapytania autonomiczne, które nie generują tych `DbDirect` metod.

## <a name="send-commands-directly-to-a-database"></a>Wysyłanie poleceń bezpośrednio do bazy danych

Wywołaj `DbDirect` metodę TableAdapter, która wykonuje zadanie, które próbujesz wykonać.

### <a name="to-insert-new-records-directly-into-a-database"></a>Aby wstawić nowe rekordy bezpośrednio do bazy danych

- Wywołaj metodę TableAdapter `Insert` , przekazując wartości dla każdej kolumny jako parametry. Poniższa procedura używa `Region` tabeli w bazie danych Northwind jako przykładu.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Aby zaktualizować rekordy bezpośrednio w bazie danych

- Wywołaj metodę TableAdapter `Update` , przekazując nowe i oryginalne wartości dla każdej kolumny jako parametry.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Aby usunąć rekordy bezpośrednio z bazy danych

- Wywołaj metodę TableAdapter `Delete` , przekazując wartości dla każdej kolumny jako parametry `Delete` metody. Poniższa procedura używa `Region` tabeli w bazie danych Northwind jako przykładu.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Zobacz też

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
