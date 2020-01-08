---
title: Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5e11feefc6e513dcaffa92389946ffef51f10d4a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586149"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych

Ten komunikat jest wyświetlany, gdy przeciągasz elementy, które nie używają Dostawca danych .NET Framework na potrzeby SQL Server z **Eksplorator serwera** lub **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Projektant O/R** obsługuje tylko połączenia danych, które używają .NET Framework dostawcy do SQL Server. Prawidłowe są tylko połączenia z plikiem bazy danych Microsoft SQL Server lub Microsoft SQL Server.

Aby naprawić ten błąd, należy dodać tylko elementy z połączeń danych, które używają Dostawca danych .NET Framework na potrzeby SQL Server do **projektanta o/R**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlClient>
- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
