---
title: 'Błąd: Microsoft Visual Studio Monitor zdalnego debugowania na komputerze zdalnym działa jako inny użytkownik | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dffaafbca80828a7501f5f7d24e525225284f5a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697307"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) na komputerze zdalnym pracuje jako inny użytkownik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas próby debugowania zdalnego może zostać wyświetlony następujący komunikat o błędzie:  
  
 Microsoft Visual Studio Monitor zdalnego debugowania na komputerze zdalnym działa jako inny użytkownik.  
  
## <a name="cause"></a>Przyczyna  
 Ten komunikat występuje w przypadku debugowania w trybie bez uwierzytelniania, a użytkownik, który uruchomił msvsmon, nie jest użytkownikiem, który uruchamia program Visual Studio.  
  
## <a name="solution"></a>Rozwiązanie  
 Najbezpieczniejszym i najlepszym rozwiązaniem jest uruchomienie Monitor zdalnego debugowania (msvsmon.exe) w ramach tego samego konta użytkownika co program Visual Studio. Jeśli nie możesz tego zrobić, możesz uruchomić Monitor zdalnego debugowania na drugim koncie z opcją **Zezwalaj każdemu użytkownikowi na Debugowanie** zaznaczonej w oknie dialogowym **Opcje** Monitor zdalnego debugowania.  
  
> [!CAUTION]
> Przyznanie innym użytkownikom uprawnień do nawiązania połączenia pozwala na przypadkowe połączenie się z nieprawidłową sesją zdalnego debugowania. Debugowanie w trybie **bez uwierzytelniania** nigdy nie jest bezpieczne i powinno być używane z zachowaniem ostrożności.  
  
 Aby uzyskać więcej informacji, zobacz [rozpoczynanie Monitor zdalnego debugowania](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
