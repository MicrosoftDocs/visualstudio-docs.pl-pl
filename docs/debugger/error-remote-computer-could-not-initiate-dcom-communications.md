---
title: Komputer zdalny nie może zainicjować komunikacji DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
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
ms.openlocfilehash: 92a03c89cfd1bf0e0772d1a1728ffb9b0754d089
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852592"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Błąd: Zdalny komputer nie mógł zainicjować komunikacji DCOM
Wystąpił błąd DCOM, gdy maszyna zdalna próbowała komunikować się z maszyną lokalną. Komputer lokalny jest maszyną, która jest

 Uruchamianie programu Visual Studio. Ten błąd może wystąpić z kilku powodów:

- Na komputerze lokalnym jest włączona Zapora.

- Uwierzytelnianie systemu Windows z komputera zdalnego na komputerze lokalnym nie działa.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Jeśli na komputerze lokalnym jest włączona Zapora systemu Windows, zobacz [debugowanie zdalne](../debugger/remote-debugging.md) , aby uzyskać instrukcje dotyczące sposobu konfigurowania zapory na potrzeby debugowania lokalnego.

2. Przetestuj uwierzytelnianie systemu Windows, próbując otworzyć udział plików na komputerze lokalnym z serwera zdalnego.

3. Aby przywrócić uwierzytelnianie systemu Windows, spróbuj ponownie uruchomić obie maszyny. Należy przejrzeć dzienniki zdarzeń na maszynach lokalnych i zdalnych pod kątem błędów protokołu Kerberos i skontaktować się z administratorami domeny w poszukiwaniu znanych problemów.

## <a name="see-also"></a>Zobacz także
 [Debugowanie zdalne](../debugger/remote-debugging.md)