---
title: Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
description: Bezpośredni dostęp do bazy danych za pomocą TableAdapter przy użyciu metod takich jak INSERT, Update i DELETE w celu manipulowania danymi bezpośrednio w bazie danych.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30248632eacde07cfcc94213aeeb75ecac8dcf70
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215919"
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

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>Aby zaktualizować rekordy bezpośrednio w bazie danych

- Wywołaj metodę TableAdapter `Update` , przekazując nowe i oryginalne wartości dla każdej kolumny jako parametry.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>Aby usunąć rekordy bezpośrednio z bazy danych

- Wywołaj metodę TableAdapter `Delete` , przekazując wartości dla każdej kolumny jako parametry `Delete` metody. Poniższa procedura używa `Region` tabeli w bazie danych Northwind jako przykładu.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>Zobacz też

- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
