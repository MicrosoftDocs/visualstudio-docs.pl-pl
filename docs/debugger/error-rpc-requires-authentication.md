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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09901453fc602deaa509ceb15e4c571764d407a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871379"
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
Debuger programu Visual Studio nie może nawiązać połączenia z komputerem zdalnym. Zasady zdalnego wywoływania procedur są włączone na komputerze lokalnym, który uniemożliwia debugowanie zdalne.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Uruchom `\` *windir*`\system32\regedt32.exe`

2. Znajdź i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Uruchom ponownie komputer, aby zmiana rejestru zaczęła obowiązywać.

4. Jeśli problem będzie nadal występować, skontaktuj się z administratorem domeny, **Aby uzyskać konfigurację komputera > Szablony administracyjne > System > zdalnego wywołania procedury > ograniczenia dla nieuwierzytelnionych klientów RPC** ustawienie zasad grupy.