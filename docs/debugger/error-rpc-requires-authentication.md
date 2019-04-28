---
title: 'Błąd: RPC wymaga uwierzytelnienia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
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
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850456"
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
Debuger programu Visual Studio nie może połączyć się z komputerem zdalnym. Na komputerze lokalnym, która uniemożliwia zdalne debugowanie jest włączona zasada rcp.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Uruchom `\` *windir*`\system32\regedt32.exe`

2. Zlokalizuj i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Aby zmiany w rejestrze zostaną wprowadzone, uruchom ponownie komputer.

4. Jeśli problem będzie się powtarzać, skontaktuj się z administratorem domeny o **Konfiguracja komputera > Szablony administracyjne > System > Remote Procedure Call > ograniczenia dotyczące nieuwierzytelnionych klientów RPC** zasad grupy ustawienie.