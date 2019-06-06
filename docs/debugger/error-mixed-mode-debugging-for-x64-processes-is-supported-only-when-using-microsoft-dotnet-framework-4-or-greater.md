---
title: 'Błąd: Trybu mieszanego debugowania x64 procesów jest obsługiwana tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9ef0daf5fd28bd829edcdce412839b03ed8347bf
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745440"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Błąd: Debugowanie procesów 64-bitowych w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
Aby debugować kod mieszany natywnych i zarządzanych w procesie 64-bitowym, konieczne jest posiadanie .NET Framework w wersji 4. Debugowanie w trybie mieszanym dla procesów 64-bitowych z .NET Framework w wersji wcześniejszej niż 4 nie jest obsługiwane.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Wykonaj jedną z następujących czynności:

  - Uaktualnić używany program .NET Framework w wersji 4.

  - Twórz 32-bitowej wersji aplikacji do debugowania.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)