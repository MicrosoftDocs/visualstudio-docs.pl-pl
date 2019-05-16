---
title: Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d2812e316d17c347341e97ec9594162a2252e4d0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688221"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Obsługuje tylko .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>). Chociaż możesz kliknąć pozycję **OK** i kontynuować pracę z obiektami od dostawców nieobsługiwanej bazy danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.  
  
> [!NOTE]
> Obsługiwane są tylko połączenia danych korzystających z .NET Framework Data Provider for SQL Server.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Kliknij przycisk **OK** kontynuować projektowania klas jednostek, które mapują do połączenia, który używa nieobsługiwanego dostawcy bazy danych. Może wystąpić nieoczekiwane zachowanie, gdy używasz nieobsługiwanej bazy danych dostawcy.  
  
     —lub—  
  
- Kliknij przycisk **anulować**.  
  
     Akcja została zatrzymana. Utwórz lub użyj połączenia danych, która używa dostawcy programu .NET Framework dla programu SQL Server.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Dostawcy danych .NET Framework](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   