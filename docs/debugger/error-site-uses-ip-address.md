---
title: 'Błąd: witryna używa adresu IP | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 96786efad0349dec7c9e8e9a02cca40af3668341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737497"
---
# <a name="error-site-uses-ip-address"></a>Błąd: witryna korzysta z adresu IP
Ten błąd występuje, gdy debuger próbuje automatycznie dołączyć do aplikacji sieci Web, która korzysta z adresu IP. Dzieje się tak, jeśli zmienisz **tożsamość witryny sieci Web** tak, aby **używała określonego adresu IP** w usługach IIS.

 Aby automatycznie dołączyć do pracy, musisz utworzyć projekt z określonym adresem IP, a nie tylko nazwą komputera. W przeciwnym razie debuger zmieni nazwę komputera na localhost, co spowoduje niepowodzenie wysłania zlecenia debugowania do usług IIS.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Zamiast tego użyj opcji dołączania ręcznego (z menu Debuguj wybierz **Dołącz do procesu**).

     —lub—

2. Zmień ustawienie **identyfikacji witryny sieci Web usług IIS** .

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji internetowych: błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)