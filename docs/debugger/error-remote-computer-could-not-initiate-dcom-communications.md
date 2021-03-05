---
description: Wystąpił błąd DCOM, gdy maszyna zdalna próbowała komunikować się z maszyną lokalną.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86d6c46f338d789d6b113551ac9d99c681290526
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146785"
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

## <a name="see-also"></a>Zobacz też
 [Debugowanie zdalne](../debugger/remote-debugging.md)
