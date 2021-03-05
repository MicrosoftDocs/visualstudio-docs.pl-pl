---
description: Ten błąd występuje, gdy użytkownik próbujący uruchomić program Visual Studio Monitor zdalnego debugowania (msvsmon) nie ma konta na komputerze lokalnym.
title: Monitor zdalnego debugowania programu Microsoft Visual Studio na komputerze zdalnym nie ma uprawnień do połączenia z tym komputerem
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f35db1d84d0f44eedbc8bf09f1e5ff9a6f49e5f2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146734"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Błąd: Monitor debugera zdalnego Microsoft Visual Studio na komputerze zdalnym nie ma uprawnień do połączenia z tym komputerem

Ten błąd występuje, gdy użytkownik próbujący uruchomić program Visual Studio Monitor zdalnego debugowania (msvsmon) nie ma konta na komputerze lokalnym. Ten błąd może wystąpić podczas debugowania zdalnego przy użyciu starszego aparatu debugowania.

## <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem

- Dodaj konto użytkownika do komputera hosta debugera programu Visual Studio z tą samą nazwą i hasłem, co konto użytkownika z systemem msvsmon na komputerze zdalnym,

   \- oraz

- Uruchom msvsmon jako użytkownika, który ma uprawnienia do wywoływania do komputera lokalnego. Oznacza to, że użytkownik musi być użytkownikiem domeny i administratorem na komputerze msvsmon. Można określić konto użytkownika do uruchamiania msvsmon na jeden z dwóch sposobów:

  - Kliknij prawym przyciskiem myszy ikonę msvsmon i wybierz polecenie **Uruchom jako** w menu skrótów.

    \- oraz

  - W wierszu polecenia Uruchom polecenie `runas.exe` .

## <a name="see-also"></a>Zobacz też

- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
