---
title: Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8030bd857f54220f23a5e8dbbf71bb377d58030b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648689"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Obsługuje tylko .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>). Chociaż możesz kliknąć pozycję **OK** i kontynuować pracę z obiektami od dostawców nieobsługiwanej bazy danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.  
  
> [!NOTE]
>  Obsługiwane są tylko połączenia danych korzystających z .NET Framework Data Provider for SQL Server.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Kliknij przycisk **OK** kontynuować projektowania klas jednostek, które mapują do połączenia, który używa nieobsługiwanego dostawcy bazy danych. Może wystąpić nieoczekiwane zachowanie, gdy używasz nieobsługiwanej bazy danych dostawcy.  
  
     —lub—  
  
-   Kliknij przycisk **anulować**.  
  
     Akcja została zatrzymana. Utwórz lub użyj połączenia danych, która używa dostawcy programu .NET Framework dla programu SQL Server.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Dostawcy danych .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   