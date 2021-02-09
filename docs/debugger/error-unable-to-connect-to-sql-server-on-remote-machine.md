---
title: Nie można nawiązać połączenia z SQL Server na maszynie zdalnej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlle_dcom_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a0fccfd97024a7e37cea772a820033786e662ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871081"
---
# <a name="error-unable-to-connect-to-sql-server-on-remote-machine"></a>Błąd: Nie można połączyć się z serwerem SQL na zdalnym komputerze
Nie można nawiązać połączenia z SQL Server na zdalnej *nazwie* maszyny. Odmowa dostępu. Sprawdź, czy na maszynie zdalnej zainstalowano zdalny debuger. Jeśli maszyna zdalna nie znajduje się w domenie lub jeśli program Visual Studio jest uruchomiony jako konto lokalne, maszyna zdalna musi mieć konto z tą samą nazwą użytkownika i hasłem co konto lokalne.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6(v=vs.100))