---
title: 'Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio na komputerze zdalnym jest uruchomiony przy użyciu konta innego użytkownika'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 513d05149ca52e1d2ec1ca057cca722cef097bd1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034850"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio na komputerze zdalnym jest uruchomiony przy użyciu konta innego użytkownika
Podczas próby przeprowadzać debugowanie zdalne, może pojawić się następujący komunikat o błędzie:  
  
 Microsoft Visual Studio zdalny Monitor debugowania programu na komputerze zdalnym jest uruchomiony jako inny użytkownik.  
  
## <a name="cause"></a>Przyczyna  
 Komunikat jest wyświetlany podczas debugowania w trybie bez uwierzytelnienia i użytkownika, który uruchomił polecenie msvsmon nie jest użytkownik, który jest uruchomiony program Visual Studio.  
  
## <a name="solution"></a>Rozwiązanie  
 Aby uruchomić Monitor zdalnego debugowania (msvsmon.exe) jest najbezpieczniejszy i najlepsze rozwiązania, w ramach tego samego konta użytkownika, co program Visual Studio. Jeśli nie możesz tego zrobić, można uruchomić Monitor zdalnego debugowania w ramach konta z **Zezwalaj dowolnemu użytkownikowi na debugowanie** opcji wybranej w monitorze debugera zdalnego **opcje** okno dialogowe.  
  
> [!CAUTION]
>  Udzielanie innym użytkownikom uprawnień do łączenia się temu możliwości przypadkowe łączenie się problem zdalnej sesji debugowania. Debugowanie w **bez uwierzytelniania** tryb nigdy nie jest bezpieczna i należy używać ostrożnie.
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)