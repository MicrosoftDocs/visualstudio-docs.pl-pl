---
title: Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667198"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten komunikat jest wyświetlany, gdy przeciągasz elementy, które nie używają Dostawca danych .NET Framework na potrzeby SQL Server z **Eksplorator serwera** /**Eksplorator bazy danych** do [narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

 @No__t_0 obsługuje tylko połączenia danych, które używają dostawcy .NET Framework do SQL Server. Prawidłowe są tylko połączenia z plikiem bazy danych Microsoft SQL Server lub Microsoft SQL Server.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Dodaj tylko elementy z połączeń danych, które używają Dostawca danych .NET Framework, aby SQL Server do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="see-also"></a>Zobacz też
 <xref:System.Data.SqlClient> [.NET Framework dostawców danych](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)