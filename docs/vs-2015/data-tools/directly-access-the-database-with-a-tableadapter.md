---
title: Bezpośrednio dostęp do bazy danych za pomocą TableAdapter | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 924a14cc3938420f32a1a2c25265ebe94e261b15
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431961"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oprócz `InsertCommand`, `UpdateCommand`, i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które można uruchamiać bezpośrednio w bazie danych. Te metody (`TableAdapter.Insert`, `TableAdapter.Update`, i `TableAdapter.Delete`) może być wywoływana można manipulować danymi bezpośrednio w bazie danych.  
  
 Jeśli nie chcesz utworzyć te metody bezpośrednie, ustaw TableAdapter `GenerateDbDirectMethods` właściwości `false` w **właściwości** okna. Wszelkie zapytania są dodawane do TableAdapter oprócz zapytanietableadapter głównym, są zapytania autonomicznych, które nie Generuj te dbdirect — metody.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly do bazy danych  
 Wywołaj metodę TableAdapter DbDirect, która wykonuje zadanie, które mają być osiągnięte.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Aby wstawić nowe rekordy bezpośrednio do bazy danych  
  
- Wywołaj TableAdapter `Insert` jest metoda wartości dla każdej kolumny jako parametry. W poniższej procedurze użyto `Region` tabelę Northwind databaseas przykładem.  
  
    > [!NOTE]
    > Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Do aktualizowania rekordów bezpośrednio w bazie danych  
  
- Wywołaj TableAdapter `Update` jest metoda nowymi i oryginalnymi wartości dla każdej kolumny jako parametry.  
  
    > [!NOTE]
    > Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Do usuwania rekordów bezpośrednio z bazy danych  
  
- Wywołaj TableAdapter `Delete` jest metoda wartości dla każdej kolumny jako parametry `Delete` metody. W poniższej procedurze użyto `Region` tabelę Northwind databaseas przykładem.  
  
    > [!NOTE]
    > Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
