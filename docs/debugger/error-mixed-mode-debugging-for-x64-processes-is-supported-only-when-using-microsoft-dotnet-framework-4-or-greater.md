---
title: Błąd — debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z Microsoft .NET Framework 4 lub nowszego | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 9f30fe9b729df84506f6717e5fd895297390dea6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460640"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Błąd: debugowanie w trybie mieszanym dla procesów x64 jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
Aby debugować mieszany kod natywny i zarządzany w procesie 64-bitowym, musisz mieć .NET Framework w wersji 4. Debugowanie w trybie mieszanym 64-bitowych procesów z .NET Framework wersjami wcześniejszymi niż 4 nie jest obsługiwane.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Wykonaj jedną z następujących czynności:

  - Uaktualnij .NET Framework do wersji 4.

  - Utwórz 32-bitową wersję aplikacji na potrzeby debugowania.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)