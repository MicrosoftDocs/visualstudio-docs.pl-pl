---
title: 'Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio na komputerze zdalnym nie ma uprawnień do połączenia z tym komputerem'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80db9cb0e29f2664a02ada17398d5dca8912a0f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002421"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio na komputerze zdalnym nie ma uprawnień do połączenia z tym komputerem
Ten błąd występuje, gdy użytkownik, który próbuje uruchomić zdalny Monitor debugowania Visual Studio (msvsmon) nie ma konta na komputerze lokalnym.  
  
### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem  
  
- Dodaj konto użytkownika do komputera hosta debugera programu Visual Studio, z taką samą nazwę i hasło jako konta użytkownika uruchamiającego polecenie msvsmon na komputerze zdalnym  
  
   \- lub —  
  
- Uruchom polecenie msvsmon jako użytkownik, który ma uprawnienia do wywołania na komputerze lokalnym. Oznacza to, że użytkownik musi być użytkownikiem domeny oraz administratorem na komputerze polecenia msvsmon. Można określić konto użytkownika, uruchom polecenie msvsmon w jeden z dwóch sposobów:  
  
  - Kliknij prawym przyciskiem myszy ikonę msvsmon, a następnie wybierz **Uruchom jako** menu skrótów  
  
    \- lub —  
  
  - W wierszu polecenia Uruchom `runas.exe`.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)