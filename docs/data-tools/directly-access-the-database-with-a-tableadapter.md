---
title: Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c6185103daab7d030787bd6f4f4f125b0fb8bcdb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997159"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter

Oprócz `InsertCommand`, `UpdateCommand`, i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które można uruchamiać bezpośrednio w bazie danych. Może wywoływać te metody (`TableAdapter.Insert`, `TableAdapter.Update`, i `TableAdapter.Delete`) można manipulować danymi bezpośrednio w bazie danych.

Jeśli nie chcesz utworzyć te metody bezpośrednie, ustaw TableAdapter `GenerateDbDirectMethods` właściwości `false` w **właściwości** okna. Jeśli wszelkie zapytania są dodawane do TableAdapter oprócz zapytanietableadapter głównym, są one zapytania autonomicznych, które nie generują one `DbDirect` metody.

## <a name="send-commands-directly-to-a-database"></a>Wysyłanie poleceń bezpośrednio do bazy danych

Wywołanie elementu TableAdapter `DbDirect` metodę, która wykonuje zadanie, który próbujesz osiągnąć.

### <a name="to-insert-new-records-directly-into-a-database"></a>Aby wstawić nowe rekordy bezpośrednio do bazy danych

-   Wywołaj TableAdapter `Insert` jest metoda wartości dla każdej kolumny jako parametry. W poniższej procedurze użyto `Region` tabeli w bazie danych Northwind jako przykład.

    > [!NOTE]
    > Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Do aktualizowania rekordów bezpośrednio w bazie danych

-   Wywołaj TableAdapter `Update` jest metoda nowymi i oryginalnymi wartości dla każdej kolumny jako parametry.

    > [!NOTE]
    > Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Do usuwania rekordów bezpośrednio z bazy danych

-   Wywołaj TableAdapter `Delete` jest metoda wartości dla każdej kolumny jako parametry `Delete` metody. W poniższej procedurze użyto `Region` tabeli w bazie danych Northwind jako przykład.

    > [!NOTE]
    > Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)