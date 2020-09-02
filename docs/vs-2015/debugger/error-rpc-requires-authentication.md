---
title: 'Błąd: RPC wymaga uwierzytelnienia | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535739"
---
# <a name="error-rpc-requires-authentication"></a>Błąd: RPC wymaga uwierzytelnienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio nie może nawiązać połączenia z komputerem zdalnym. Zasady zdalnego wywoływania procedur są włączone na komputerze lokalnym, który uniemożliwia debugowanie zdalne.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Uruchom `\` *windir*`\system32\regedt32.exe`  
  
2. Znajdź i Usuń `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .  
  
3. Uruchom ponownie komputer, aby zmiana rejestru zaczęła obowiązywać.  
  
4. Jeśli problem będzie się powtarzać, skontaktuj się z administratorem domeny, aby uzyskać informacje na temat **konfiguracji komputera->Szablony administracyjne->system->zdalne wywołanie procedury->ograniczenia dotyczące nieuwierzytelnionych klientów RPC** ustawienie zasad grupy.
