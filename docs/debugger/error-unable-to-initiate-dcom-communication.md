---
title: Nie można zainicjować komunikacji DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 00846f0ef0593ec7d12c657a40079ff1cdfb0bb5
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851440"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Błąd: nie można zainicjować komunikacji DCOM
Wystąpił błąd DCOM, gdy komputer lokalny próbował się skomunikować z maszyną zdalną. Jest to spowodowane przez zaporę na serwerze zdalnym lub uszkodzenie uwierzytelniania systemu Windows na maszynie zdalnej.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Jeśli na komputerze zdalnym jest włączona Zapora systemu Windows, zobacz [debugowanie zdalne](../debugger/remote-debugging.md) , aby uzyskać instrukcje dotyczące sposobu konfigurowania zapory na potrzeby debugowania lokalnego.

- Aby przywrócić uwierzytelnianie systemu Windows, spróbuj ponownie uruchomić obie maszyny. Należy przejrzeć dzienniki zdarzeń na maszynach lokalnych i zdalnych pod kątem błędów protokołu Kerberos i skontaktować się z administratorami domeny w poszukiwaniu znanych problemów.

## <a name="see-also"></a>Zobacz także
- [Debugowanie zdalne](../debugger/remote-debugging.md)