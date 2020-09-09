---
title: Błąd — użytkownik nie może wykonać procedury składowanej sp_enable_sql_debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84326c5c1beb91269a5f097c8c5d7cb8782a7a56
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600146"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Błąd: użytkownik nie mógł wykonać procedury przechowywanej sp_enable_sql_debug

Nie można wykonać procedury składowanej sp_enable_sql_debug na serwerze. Może to być spowodowane przez:

- Problem z połączeniem. Musisz mieć stabilne połączenie z serwerem.

- Brak wymaganych uprawnień na serwerze. Aby debugować na SQL Server 2005, zarówno konto z programem Visual Studio, jak i konto używane do nawiązywania połączenia z SQL Server muszą być członkami roli sysadmin. Konto używane do nawiązywania połączenia z SQL Server jest kontem użytkownika systemu Windows (Jeśli używasz uwierzytelniania systemu Windows) lub kontem z IDENTYFIKATORem użytkownika i hasłem (Jeśli używasz uwierzytelniania SQL).

Aby uzyskać więcej informacji, zobacz [How to: Set SQL Server Permissions for debug](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Ustawianie uprawnień SQL Server na potrzeby debugowania](/previous-versions/w1bhybwz(v=vs.100))
- [Konfigurowanie debugowania SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))