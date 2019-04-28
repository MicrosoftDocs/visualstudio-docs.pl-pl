---
title: 'Błąd: Witryna korzysta z adresu IP | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 468cb2c85be088213bc865122a790408c6c992b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850415"
---
# <a name="error-site-uses-ip-address"></a>Błąd: Witryna korzysta z adresu IP
Ten błąd występuje, gdy debuger próbuje automatyczne dołączanie do aplikacji sieci Web, który jest przy użyciu adresu IP. Dzieje się tak w przypadku zmiany **Identyfikacja witryny sieci Web** do **użyć określonego adresu IP** w usługach IIS.

 Aby uzyskać automatyczne dołączanie do pracy, należy utworzyć projekt z określonego adresu IP, a nie tylko nazwę maszyny. W przeciwnym razie debuger zmieni nazwę komputera, na hoście lokalnym, co spowoduje niepowodzenie wysyłania czasownik debug w usługach IIS.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Użyj ręcznie dołączyć zamiast (wybierz z menu Debugowanie **dołączyć do procesu**).

     —lub—

2. Zmiana **Identyfikacja witryny sieci Web usług IIS** ustawienie.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)