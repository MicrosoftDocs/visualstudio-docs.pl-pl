---
title: 'Błąd: Nie można zainicjować komunikacji DCOM | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: 1dc250666c5f60064016b90121f7238f9e6e19ae
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682723"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Błąd: Nie można zainicjować komunikacji DCOM
Wystąpił błąd modelu DCOM podczas próby komunikacji z komputerem zdalnym komputerze lokalnym. Jest to spowodowane przez zaporę na serwerze zdalnym lub uszkodzone uwierzytelniania Windows na komputerze zdalnym.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

-   Jeśli maszyna zdalna ma włączoną zaporę Windows, zobacz [zdalne debugowanie](../debugger/remote-debugging.md) instrukcje dotyczące sposobu konfigurowania zapory dla debugowania lokalnego.

-   Aby przywrócić uwierzytelniania Windows, spróbuj wykonać ponowny rozruch obu komputerach. Sprawdź dzienniki zdarzeń na komputerach lokalnych i zdalnych dla błędów protokołu Kerberos i skontaktuj się z administratorami domeny o znanych problemach.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)