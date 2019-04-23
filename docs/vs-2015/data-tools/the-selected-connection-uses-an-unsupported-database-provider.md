---
title: Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3db964387209b833437e1ffc4dbc3a26689729ed
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061416"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa nieobsługiwanego dostawcy bazy danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten komunikat pojawia się podczas przeciągania elementów, które nie korzystają z dostawcy danych .NET Framework dla programu SQL Server z **Eksploratora serwera**/**Eksplorator bazy danych** na [LINQ to SQL Narzędzia programu Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Obsługuje tylko połączenia danych, które używają dostawcy programu .NET Framework dla programu SQL Server. Prawidłowe są tylko połączenia do programu Microsoft SQL Server lub plik bazy danych programu Microsoft SQL Server.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj tylko elementy z połączeń danych, korzystających z .NET Framework Data Provider for SQL Server w celu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.SqlClient>   
 [Dostawcy danych .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Przewodnik: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)