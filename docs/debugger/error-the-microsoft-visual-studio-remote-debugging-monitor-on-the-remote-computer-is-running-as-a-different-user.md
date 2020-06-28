---
title: Błąd — Monitor zdalnego debugowania Microsoft Visual Studio na komputerze zdalnym działa jako inny użytkownik
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: a69745a051af0ec44eb813054e40fb9f6c6a0aa6
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460406"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) na komputerze zdalnym pracuje jako inny użytkownik
Podczas próby debugowania zdalnego może zostać wyświetlony następujący komunikat o błędzie:

 Microsoft Visual Studio Monitor zdalnego debugowania na komputerze zdalnym działa jako inny użytkownik.

## <a name="cause"></a>Przyczyna
 Ten komunikat występuje w przypadku debugowania w trybie bez uwierzytelniania, a użytkownik, który uruchomił msvsmon, nie jest użytkownikiem, który uruchamia program Visual Studio.

## <a name="solution"></a>Rozwiązanie
 Najbezpieczniejszym i najlepszym rozwiązaniem jest uruchomienie Monitor zdalnego debugowania (msvsmon.exe) w ramach tego samego konta użytkownika co program Visual Studio. Jeśli nie możesz tego zrobić, możesz uruchomić Monitor zdalnego debugowania na drugim koncie z opcją **Zezwalaj każdemu użytkownikowi na Debugowanie** zaznaczonej w oknie dialogowym **Opcje** Monitor zdalnego debugowania.

> [!CAUTION]
> Przyznanie innym użytkownikom uprawnień do nawiązania połączenia pozwala na przypadkowe połączenie się z nieprawidłową sesją zdalnego debugowania. Debugowanie w trybie **bez uwierzytelniania** nigdy nie jest bezpieczne i powinno być używane z zachowaniem ostrożności.

## <a name="see-also"></a>Zobacz też
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)