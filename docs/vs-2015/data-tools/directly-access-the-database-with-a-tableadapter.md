---
title: Bezpośredni dostęp do bazy danych za pomocą TableAdapter | Microsoft Docs
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657374"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oprócz `InsertCommand` , `UpdateCommand` , i `DeleteCommand` , TableAdapters są tworzone przy użyciu metod, które mogą być uruchamiane bezpośrednio w bazie danych. Te metody ( `TableAdapter.Insert` , `TableAdapter.Update` i `TableAdapter.Delete` ) mogą być wywoływane w celu manipulowania danymi bezpośrednio w bazie danych.

 Jeśli nie chcesz tworzyć tych metod bezpośrednich, ustaw `GenerateDbDirectMethods` Właściwość TableAdapter `false` w oknie **Właściwości** . Jeśli jakiekolwiek zapytania zostaną dodane do TableAdapter oprócz głównego zapytania TableAdapter, są to zapytania autonomiczne, które nie generują tych metod DBDirect.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly do bazy danych
 Wywołaj metodę TableAdapter DBDirect, która wykonuje zadanie, które próbujesz wykonać.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Aby wstawić nowe rekordy bezpośrednio do bazy danych

- Wywołaj metodę TableAdapter `Insert` , przekazując wartości dla każdej kolumny jako parametry. Poniższa procedura używa `Region` tabeli w przykładzie Northwind databaseas.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Aby zaktualizować rekordy bezpośrednio w bazie danych

- Wywołaj metodę TableAdapter `Update` , przekazując nowe i oryginalne wartości dla każdej kolumny jako parametry.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Aby usunąć rekordy bezpośrednio z bazy danych

- Wywołaj metodę TableAdapter `Delete` , przekazując wartości dla każdej kolumny jako parametry `Delete` metody. Poniższa procedura używa `Region` tabeli w przykładzie Northwind databaseas.

    > [!NOTE]
    > Jeśli nie masz dostępnego wystąpienia, Utwórz wystąpienie TableAdapter, którego chcesz użyć.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Zobacz też
 [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
