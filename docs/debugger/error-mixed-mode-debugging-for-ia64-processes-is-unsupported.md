---
title: 'Błąd: debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
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
ms.openlocfilehash: 0bddbb1572bd0258eae2052eb34dfa3d0d67a134
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737622"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Błąd: debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwane
Debuger [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie obsługuje debugowania kodu natywnego i zarządzanego w procesie opartym na architekturze Itanium.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Utwórz 32-bitową wersję aplikacji na potrzeby debugowania.

## <a name="see-also"></a>Zobacz także
- [Debugowanie zdalne](../debugger/remote-debugging.md)