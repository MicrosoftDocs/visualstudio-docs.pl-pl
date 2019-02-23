---
title: 'Błąd: Debugowanie w trybie mieszanym dla procesów IA64 nie jest obsługiwany | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: f80cc0d38335679df413f104deadc8f9135ab765
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715755"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Błąd: Debugowanie procesów IA64 w trybie mieszanym nie jest obsługiwane
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger nie obsługuje debugowania kod mieszany natywnych i zarządzanych w procesie opartych na procesorach Itanium.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

-   Twórz 32-bitowej wersji aplikacji do debugowania.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)