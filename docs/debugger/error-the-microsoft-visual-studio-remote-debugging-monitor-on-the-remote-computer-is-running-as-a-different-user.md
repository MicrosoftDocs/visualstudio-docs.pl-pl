---
title: 'Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) na komputerze zdalnym pracuje jako inny użytkownik'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1cb477cf852d0e07bf14f344b3dc27b20a56de59
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067736"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) na komputerze zdalnym pracuje jako inny użytkownik
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