---
title: Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4efaf92c9f4688d6870c1152be27eb4c8f4ed933
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894444"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych

**O/R Designer** obsługuje tylko .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>). Chociaż możesz kliknąć pozycję **OK** i kontynuować pracę z obiektami od dostawców nieobsługiwanej bazy danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.

> [!NOTE]
> Obsługiwane są tylko połączenia danych korzystających z .NET Framework Data Provider for SQL Server.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Kliknij przycisk **OK**.

   Aby kontynuować, projektowania klas jednostek, które mapują do połączenia, który używa nieobsługiwanego dostawcy bazy danych. Może wystąpić nieoczekiwane zachowanie, gdy używasz nieobsługiwanej bazy danych dostawcy.

    —lub—

- Kliknij przycisk **anulować**.

   Akcja została zatrzymana. Utwórz lub użyj połączenia danych, która używa dostawcy programu .NET Framework dla programu SQL Server.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)