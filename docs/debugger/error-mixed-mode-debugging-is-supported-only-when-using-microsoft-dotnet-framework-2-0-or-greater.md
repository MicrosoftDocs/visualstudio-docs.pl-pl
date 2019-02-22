---
title: 'Błąd: Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework w wersji 2.0 lub nowszej wersji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
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
ms.openlocfilehash: 2fb4d0dfaeb944700757c9ceec222dbd62dab9dd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681156"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Błąd: Debugowanie w trybie mieszanym jest obsługiwane tylko w przypadku korzystania z programu Microsoft .NET Framework 2.0 lub nowszej wersji
Aby debugować kod mieszany natywnych i zarządzanych, konieczne jest posiadanie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji 2.0, 3.0 lub nowszej. 3.5 lub 4.0. Debugowanie w trybie mieszanym z wcześniejszymi wersjami programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nie jest obsługiwane.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Uaktualnij [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] do wersji 2.0, 3.0, 3.5 lub 4.0.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)