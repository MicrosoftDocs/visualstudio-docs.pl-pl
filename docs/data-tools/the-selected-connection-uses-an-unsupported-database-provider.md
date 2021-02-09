---
title: Nieobsługiwany dostawca bazy danych
description: Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych. Wyświetl informacje o tym komunikacie Object Relational Designer programu Visual Studio (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 246559abc0d1cbc12754b708bbc5938e9e190ddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858308"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych

Ten komunikat jest wyświetlany, gdy przeciągasz elementy, które nie używają Dostawca danych .NET Framework na potrzeby SQL Server z **Eksplorator serwera** lub **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Projektant O/R** obsługuje tylko połączenia danych, które używają .NET Framework dostawcy do SQL Server. Prawidłowe są tylko połączenia z plikiem bazy danych Microsoft SQL Server lub Microsoft SQL Server.

Aby naprawić ten błąd, należy dodać tylko elementy z połączeń danych, które używają Dostawca danych .NET Framework na potrzeby SQL Server do **projektanta o/R**.

## <a name="see-also"></a>Zobacz też

- <xref:System.Data.SqlClient>
- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
