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
ms.openlocfilehash: 0bf72110e82fc3cd920f571a5630faafbf2aa5ec
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696535"
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
Debuger programu Visual Studio nie może połączyć się z komputerem zdalnym. Na komputerze lokalnym, która uniemożliwia zdalne debugowanie jest włączona zasada rcp.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1.  Uruchom `\` *windir*`\system32\regedt32.exe`

2.  Zlokalizuj i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3.  Aby zmiany w rejestrze zostaną wprowadzone, uruchom ponownie komputer.

4.  Jeśli problem będzie się powtarzać, skontaktuj się z administratorem domeny o **Konfiguracja komputera > Szablony administracyjne > System > Remote Procedure Call > ograniczenia dotyczące nieuwierzytelnionych klientów RPC** zasad grupy ustawienie.