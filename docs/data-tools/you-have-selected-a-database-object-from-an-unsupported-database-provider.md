---
title: Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13e6dd42ed372fb28d850a566ea1900447ad220c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909518"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych

**O/R Designer** obsługuje tylko .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>). Chociaż możesz kliknąć pozycję **OK** i kontynuować pracę z obiektami od dostawców nieobsługiwanej bazy danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.

> [!NOTE]
> Obsługiwane są tylko połączenia danych korzystających z .NET Framework Data Provider for SQL Server.

## <a name="options"></a>Opcje

- Kliknij przycisk **OK** kontynuować projektowania klas jednostek, które mapują do połączenia, który używa nieobsługiwanego dostawcy bazy danych. Może wystąpić nieoczekiwane zachowanie, gdy używasz nieobsługiwanej bazy danych dostawcy.

- Kliknij przycisk **anulować** zatrzymania działania. Utwórz lub użyj innego połączenia danych, która używa .NET Framework Provider for SQL Server.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)