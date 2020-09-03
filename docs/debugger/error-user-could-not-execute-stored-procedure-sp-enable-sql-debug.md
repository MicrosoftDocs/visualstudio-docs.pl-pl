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
ms.openlocfilehash: c1da494b5bb8c168775e2183f41113f00d021792
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460068"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Błąd: użytkownik nie mógł wykonać procedury przechowywanej sp_enable_sql_debug

Nie można wykonać procedury składowanej sp_enable_sql_debug na serwerze. Może to być spowodowane przez:

- Problem z połączeniem. Musisz mieć stabilne połączenie z serwerem.

- Brak wymaganych uprawnień na serwerze. Aby debugować na SQL Server 2005, zarówno konto z programem Visual Studio, jak i konto używane do nawiązywania połączenia z SQL Server muszą być członkami roli sysadmin. Konto używane do nawiązywania połączenia z SQL Server jest kontem użytkownika systemu Windows (Jeśli używasz uwierzytelniania systemu Windows) lub kontem z IDENTYFIKATORem użytkownika i hasłem (Jeśli używasz uwierzytelniania SQL).

Aby uzyskać więcej informacji, zobacz [How to: Set SQL Server Permissions for debug](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Ustawianie uprawnień SQL Server na potrzeby debugowania](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Konfigurowanie debugowania SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))