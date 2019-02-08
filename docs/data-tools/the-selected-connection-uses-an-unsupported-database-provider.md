---
title: Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6ebdca67dd87f25111ba48c3d9baa346d00e4db
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923814"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych

Ten komunikat pojawia się podczas przeciągania elementów, które nie korzystają z dostawcy danych .NET Framework dla programu SQL Server z **Eksploratora serwera** lub **Eksplorator bazy danych** na [LINQ to SQL tools w wizualizacji Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**O/R Designer** obsługuje tylko połączenia danych, które używają dostawcy programu .NET Framework dla programu SQL Server. Prawidłowe są tylko połączenia do programu Microsoft SQL Server lub plik bazy danych programu Microsoft SQL Server.

Aby rozwiązać ten problem, należy dodać tylko elementy z połączeń danych, korzystających z .NET Framework Data Provider for SQL Server, aby **O/R Designer**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlClient>
- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
