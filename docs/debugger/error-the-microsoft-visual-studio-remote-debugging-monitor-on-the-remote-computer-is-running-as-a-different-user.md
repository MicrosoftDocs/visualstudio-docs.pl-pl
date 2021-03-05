---
title: Monitor zdalnego debugowania programu Microsoft Visual Studio na komputerze zdalnym jest uruchomiony przy użyciu konta innego użytkownika
titleSuffix: ''
description: Ten komunikat występuje w przypadku debugowania w trybie bez uwierzytelniania, a użytkownik, który uruchomił msvsmon, nie jest użytkownikiem, który uruchamia program Visual Studio.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cee8ea9442ab88c280a11a0b73d74cac6888e9f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146707"
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
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
