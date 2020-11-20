---
title: Nieobsługiwany dostawca bazy danych
description: Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych. Wyświetl informacje o tym komunikacie Object Relational Designer programu Visual Studio (Projektant O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 06e08f9a9c28698ae2ee2fecfbcec64c39666c8a
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998350"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych

Ten komunikat jest wyświetlany, gdy przeciągasz elementy, które nie używają Dostawca danych .NET Framework na potrzeby SQL Server z **Eksplorator serwera** lub **Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Projektant O/R** obsługuje tylko połączenia danych, które używają .NET Framework dostawcy do SQL Server. Prawidłowe są tylko połączenia z plikiem bazy danych Microsoft SQL Server lub Microsoft SQL Server.

Aby naprawić ten błąd, należy dodać tylko elementy z połączeń danych, które używają Dostawca danych .NET Framework na potrzeby SQL Server do **projektanta o/R**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlClient>
- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
