---
title: 'Błąd: wykonywanie kodu Transact-SQL zakończyło się bez debugowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdfcaa42c55f87711b0889c6a67d1a4799b84fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681076"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje podczas próby debugowania procedury języka Transact-SQL lub SQLCLR, a debuger nie odbiera komunikatów debugowania z SQL Server.  
  
 Przyczyną mogą być problemy z siecią lub problemy z SQL Server, ale najbardziej prawdopodobną przyczyną jest problem z uprawnieniami.  
  
 Istnieją dwa konta:  
  
- Konto aplikacji to konto użytkownika, na którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] działa program.  
  
- Konto połączenia to tożsamość użyta do nawiązania połączenia z SQL Server. Nie musi to być taka sama jak tożsamość, która jest uruchomiona w programie Visual Studio, jeśli połączenie korzysta z uwierzytelniania SQL.  
  
  Debugowanie SQL wymaga, aby konto aplikacji było zgodne z kontem połączenia lub administratorem systemu.  
  
  Jeśli używasz logowania SQL, takiego jak sa, konto aplikacji musi być skonfigurowane na SQL Server jako administrator. Domyślnie Administratorzy na komputerze, na którym jest uruchomiony program SQL Server, są SQL Server Sysadmins.  
  
  Aby naprawić ten błąd, może być konieczne:  
  
- Sprawdź ustawienia uprawnień. Aby uzyskać więcej informacji, zobacz [How to: Set SQL Server Permissions for debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Upewnij się, że debugowanie SQL zostało prawidłowo skonfigurowane.  
  
- Skontaktuj się z administratorem sieci lub bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie debugowania SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Instrukcje: Ustawianie uprawnień SQL Server na potrzeby debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
