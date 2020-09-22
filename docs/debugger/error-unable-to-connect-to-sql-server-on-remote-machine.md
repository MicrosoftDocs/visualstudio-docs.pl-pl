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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86f2d9397248806a4c996fabfcd20d325afbf533
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852527"
---
# <a name="error-unable-to-connect-to-sql-server-on-remote-machine"></a>Błąd: Nie można połączyć się z serwerem SQL na zdalnym komputerze
Nie można nawiązać połączenia z SQL Server na zdalnej *nazwie*maszyny. Odmowa dostępu. Sprawdź, czy na maszynie zdalnej zainstalowano zdalny debuger. Jeśli maszyna zdalna nie znajduje się w domenie lub jeśli program Visual Studio jest uruchomiony jako konto lokalne, maszyna zdalna musi mieć konto z tą samą nazwą użytkownika i hasłem co konto lokalne.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

## <a name="see-also"></a>Zobacz także
- [Debugowanie SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6(v=vs.100))