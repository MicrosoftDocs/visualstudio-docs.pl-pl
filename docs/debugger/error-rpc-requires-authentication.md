---
title: Usługa RPC wymaga uwierzytelniania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 9bb172455226ab290a74da07e97fc40deb30b6ba
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852553"
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
Debuger programu Visual Studio nie może nawiązać połączenia z komputerem zdalnym. Zasady zdalnego wywoływania procedur są włączone na komputerze lokalnym, który uniemożliwia debugowanie zdalne.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Uruchom `\` *windir*`\system32\regedt32.exe`

2. Znajdź i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Uruchom ponownie komputer, aby zmiana rejestru zaczęła obowiązywać.

4. Jeśli problem będzie nadal występować, skontaktuj się z administratorem domeny, **Aby uzyskać konfigurację komputera > Szablony administracyjne > System > zdalnego wywołania procedury > ograniczenia dla nieuwierzytelnionych klientów RPC** ustawienie zasad grupy.