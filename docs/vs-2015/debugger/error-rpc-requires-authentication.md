---
title: 'Błąd: RPC wymaga uwierzytelnienia | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102734"
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio nie może połączyć się z komputerem zdalnym. Na komputerze lokalnym, która uniemożliwia zdalne debugowanie jest włączona zasada rcp.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Uruchom `\` *windir*`\system32\regedt32.exe`  
  
2. Zlokalizuj i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3. Aby zmiany w rejestrze zostaną wprowadzone, uruchom ponownie komputer.  
  
4. Jeśli problem będzie się powtarzać, skontaktuj się z administratorem domeny o **Konfiguracja komputera -> Szablony administracyjne - > System -> zdalnego wywołania procedury -> ograniczenia dotyczące nieuwierzytelnionych klientów RPC** grupy ustawienia zasad.
