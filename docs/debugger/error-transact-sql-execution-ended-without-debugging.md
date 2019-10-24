---
title: 'Błąd: wykonywanie kodu Transact-SQL zakończyło się bez debugowania | Microsoft Docs'
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
ms.openlocfilehash: 94ced2902becc2e988cde5198eff28911864dcbb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736936"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Błąd: Wykonanie Transact-SQL zakończyło się bez debugowania

Ten błąd występuje, gdy próbujesz debugować procedurę języka Transact-SQL lub SQLCLR, a debuger nie odbiera komunikatów debugowania z SQL Server.

Przyczyną tego problemu może być problemy z siecią lub problemy z SQL Server, ale najbardziej prawdopodobną przyczyną jest problem z uprawnieniami.

Istnieją dwa konta:

- Konto aplikacji to konto użytkownika, na którym uruchomiono [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Konto połączenia to tożsamość użyta do nawiązania połączenia z SQL Server. To konto nie musi być takie samo jak tożsamość, w której działa program Visual Studio, jeśli połączenie korzysta z uwierzytelniania SQL.

  Debugowanie SQL wymaga, aby konto aplikacji było zgodne z kontem połączenia, albo być administratorem systemu.

  Jeśli używasz nazwy konta SQL, takiej jak sa, konto aplikacji musi być skonfigurowane na SQL Server jako administrator. Domyślnie Administratorzy na komputerze, na którym działa program SQL Server, są SQL Server Sysadmins.

  Aby naprawić ten błąd, może być konieczne:

  - Sprawdź ustawienia uprawnień. Aby uzyskać więcej informacji, zobacz [How to: Set SQL Server Permissions for debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Upewnij się, że debugowanie SQL zostało prawidłowo skonfigurowane.

  - Skontaktuj się z administratorem sieci lub bazy danych.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie debugowania SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Instrukcje: Ustawianie uprawnień SQL Server na potrzeby debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)