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
ms.openlocfilehash: 61c92460976ec9b95163b83744ee0b01b6ebc572
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986088"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Błąd: Debugowanie procesów 64-bitowych w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 4 lub nowszej wersji
Aby debugować kod mieszany natywnych i zarządzanych w procesie 64-bitowym, konieczne jest posiadanie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] w wersji 4. Debugowanie trybu mieszanego procesów 64-bitowe o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] w wersji wcześniejszej niż 4 nie jest obsługiwane.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Wykonaj jedną z następujących czynności:  
  
  - Uaktualnij swoje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] do wersji 4.  
  
  - Twórz 32-bitowej wersji aplikacji do debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)