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
ms.openlocfilehash: dae92f404bb9ecb23b77dbda33c329994b9ed15b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457878"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Wybrano obiekt bazy danych od nieobsługiwanego dostawcy bazy danych

**O/R Designer** obsługuje tylko .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>). Chociaż możesz kliknąć pozycję **OK** i kontynuować pracę z obiektami od dostawców nieobsługiwanej bazy danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.

> [!NOTE]
> Obsługiwane są tylko połączenia danych korzystających z .NET Framework Data Provider for SQL Server.

## <a name="options"></a>Opcje

- Kliknij przycisk **OK** kontynuować projektowania klas jednostek, które mapują do połączenia, który używa nieobsługiwanego dostawcy bazy danych. Może wystąpić nieoczekiwane zachowanie, gdy używasz nieobsługiwanej bazy danych dostawcy.

- Kliknij przycisk **anulować** zatrzymania działania. Utwórz lub użyj innego połączenia danych, która używa .NET Framework Provider for SQL Server.

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)