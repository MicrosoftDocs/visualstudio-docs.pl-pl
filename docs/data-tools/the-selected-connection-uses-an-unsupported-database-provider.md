---
title: Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 52b88e1de91c2b2da629b6b9034ac552b8d88d5d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281321"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych

Ten komunikat jest wyświetlany, gdy przeciągasz elementy, które nie używają Dostawca danych .NET Framework na potrzeby SQL Server z **Eksplorator serwera** lub **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Projektant O/R** obsługuje tylko połączenia danych, które używają .NET Framework dostawcy do SQL Server. Prawidłowe są tylko połączenia z plikiem bazy danych Microsoft SQL Server lub Microsoft SQL Server.

Aby naprawić ten błąd, należy dodać tylko elementy z połączeń danych, które używają Dostawca danych .NET Framework na potrzeby SQL Server do **projektanta o/R**.

## <a name="see-also"></a>Zobacz też

- <xref:System.Data.SqlClient>
- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
