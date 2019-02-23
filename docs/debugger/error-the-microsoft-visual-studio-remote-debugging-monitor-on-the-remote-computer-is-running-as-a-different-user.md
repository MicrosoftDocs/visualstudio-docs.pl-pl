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
ms.openlocfilehash: 5099b917ffe7d9d96174156bdb4f284ab6a4c0af
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688485"
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
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)