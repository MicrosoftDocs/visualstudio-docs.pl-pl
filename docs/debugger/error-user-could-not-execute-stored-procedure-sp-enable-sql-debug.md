---
title: 'Błąd: Użytkownik może nie wykonać procedury przechowywanej sp_enable_sql_debug | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b121b863237a3b12b5131be348581ea3fd043d2
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348570"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Błąd: Użytkownik może nie wykonać procedury przechowywanej sp_enable_sql_debug

Procedury przechowywanej sp_enable_sql_debug nie można wykonać na serwerze. Może to być spowodowane:

- Problem z połączeniem. Musisz mieć stabilne połączenie z serwerem.

- Brak wystarczających uprawnień na serwerze. Do debugowania w programie SQL Server 2005, zarówno w przypadku konta, programem Visual Studio, jak i konto używane do łączenia się z serwerem SQL muszą być członkami roli sysadmin. Konto używane do łączenia się z serwerem SQL jest kontem użytkownika Windows (Jeśli używasz uwierzytelniania Windows) lub konto z Identyfikatorem użytkownika i hasło (Jeśli używasz uwierzytelniania SQL).

Aby uzyskać więcej informacji, zobacz [jak: Ustawianie uprawnień programu SQL Server do debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Ustawianie uprawnień programu SQL Server do debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Konfigurowanie debugowania SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))