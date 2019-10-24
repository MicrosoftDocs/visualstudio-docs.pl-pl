---
title: 'Błąd: debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z Microsoft .NET Framework 4 lub nowszego | Microsoft Docs'
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
ms.openlocfilehash: 67b9d1c737e4490195b209abca824b2d6d51176c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737602"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Błąd: debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
Aby debugować mieszany kod natywny i zarządzany w procesie 64-bitowym, musisz mieć .NET Framework w wersji 4. Debugowanie w trybie mieszanym 64-bitowych procesów z .NET Framework wersjami wcześniejszymi niż 4 nie jest obsługiwane.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Wykonaj jedną z następujących czynności:

  - Uaktualnij .NET Framework do wersji 4.

  - Utwórz 32-bitową wersję aplikacji na potrzeby debugowania.

## <a name="see-also"></a>Zobacz także
- [Debugowanie zdalne](../debugger/remote-debugging.md)