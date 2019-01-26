---
title: 'Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania | Dokumentacja firmy Microsoft'
ms.date: 11/08/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17c1854826de2314dfe8124d99f6ec6c8899ee70
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011224"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Błąd: Wykonywanie kodu Transact-SQL zakończyło się bez debugowania

Ten błąd występuje podczas próby debugowania języka Transact-SQL lub procedury SQLCLR i debuger nie odbiera komunikaty debugowania z programu SQL Server.  
  
Ten problem może być z powodu problemów z siecią lub problemy w programie SQL Server, ale najbardziej prawdopodobną przyczyną jest problem z uprawnieniami.  
  
Zaangażowanych dwa konta:  
  
- Konto aplikacji znajduje się konto użytkownika, który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] działa jako.  
  
- Konto połączenia jest to tożsamość używana do nawiązywania połączeń z programem SQL Server. To konto nie jest zawsze taki sam jak tożsamość, która Visual Studio działa tak, jakby połączenie korzysta z uwierzytelniania programu SQL.  
  
  Debugowanie SQL wymaga, aby konto aplikacji musi odpowiadać kontu połączenia lub być administratorem sysadmin.  
  
  Jeśli używasz nazwy konta SQL, takich jak sa konto aplikacji można ustawić w programie SQL Server jako administrator systemu. Domyślnie administratorzy na komputerze, na którym jest uruchomiony program SQL server na są głównym programu SQL Server.  
  
  Aby naprawić ten błąd, konieczne może być:  
  
  - Sprawdź ustawienia uprawnień. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie uprawnień programu SQL Server do debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
  - Upewnij się, że debugowanie SQL, jeśli skonfigurowane prawidłowo.  
  
  - Zapoznaj się z administratorem sieci lub bazy danych.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie debugowania SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Instrukcje: Ustawianie uprawnień programu SQL Server do debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)