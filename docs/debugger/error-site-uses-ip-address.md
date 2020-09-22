---
title: Witryna używa adresu IP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b869a536ca3445069d9caf84eb862e407dfbe6dc
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852540"
---
# <a name="error-site-uses-ip-address"></a>Błąd: witryna korzysta z adresu IP
Ten błąd występuje, gdy debuger próbuje automatycznie dołączyć do aplikacji sieci Web, która korzysta z adresu IP. Dzieje się tak, jeśli zmienisz **tożsamość witryny sieci Web** tak, aby **używała określonego adresu IP** w usługach IIS.

 Aby automatycznie dołączyć do pracy, musisz utworzyć projekt z określonym adresem IP, a nie tylko nazwą komputera. W przeciwnym razie debuger zmieni nazwę komputera na localhost, co spowoduje niepowodzenie wysłania zlecenia debugowania do usług IIS.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Zamiast tego użyj opcji dołączania ręcznego (z menu Debuguj wybierz **Dołącz do procesu**).

     —lub—

2. Zmień ustawienie **identyfikacji witryny sieci Web usług IIS** .

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)