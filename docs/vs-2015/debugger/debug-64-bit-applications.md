---
title: Debuguj 64-bitowe aplikacje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0eaa719bb3eeca2eb3dfe558184699ccca42819
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387203"
---
# <a name="debug-64-bit-applications"></a>Debugowanie aplikacji 64-bitowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu można znaleźć na stronie [debugowanie 64-bitowe aplikacje](/visualstudio/debugger/debug-64-bit-applications) .  
  
Można debugować aplikację 64-bitową uruchomioną na komputerze lokalnym lub na komputerze zdalnym.  
  
 Aby debugować aplikację 64-bitową, która jest uruchomiona na komputerze zdalnym, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
 Aby lokalnie debugować aplikacje 64-bitowe, program Visual Studio korzysta z 64-bitowego procesu roboczego (msvsmon.exe) do wykonywania operacji niskiego poziomu, które nie mogą być wykonywane w ramach 32-bitowego procesu programu Visual Studio.  
  
 Debugowanie w trybie mieszanym nie jest obsługiwane w przypadku procesów 64-bitowych, które używają .NET Framework w wersji 3,5 lub starszej.  
  
## <a name="debug-a-64-bit-application"></a>Debugowanie aplikacji 64-bitowej  
 Aby spróbować debugować aplikację 64-bitową:  
  
1. Utwórz rozwiązanie programu Visual Studio, na przykład aplikację konsolową w języku C#.  
  
2. Ustaw konfigurację na 64-bitową przy użyciu Configuration Manager. Aby uzyskać więcej informacji, zobacz [How to: Configure projects to target platforms](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3. W tym momencie zostanie uruchomiona 64-bitowa wersja debugera zdalnego (msvsmon.exe). Działa tak długo, jak jest otwarte rozwiązanie z konfiguracją 64-bitową.  
  
4. Uruchom debugowanie. Powinno to być takie samo środowisko jak w przypadku konfiguracji 32-bitowej. W przypadku wystąpienia błędów zapoznaj się z sekcją Rozwiązywanie problemów poniżej.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Rozwiązywanie problemów z 64-bitowym debugowaniem  
 Może zostać wyświetlony komunikat o błędzie: "A 64-bit operacji debugowania trwa dłużej niż oczekiwano". W takim przypadku program Visual Studio wysłał żądanie do 64-bitowej wersji msvsmon.exe i pozostało dużo czasu na wynik tego żądania.  
  
 Istnieją dwa główne przyczyny tego błędu:  
  
- Na komputerze jest zainstalowane oprogramowanie zabezpieczeń sieci, które spowodowało, że stos sieciowy jest niezawodny i porzucane są pakiety przechodzące przez hosty localhost. Spróbuj wyłączyć wszystkie oprogramowanie zabezpieczeń sieci i sprawdź, czy to rozwiązanie go rozwiązuje. Jeśli tak, zgłoś dostawcę oprogramowania zabezpieczeń sieci, że oprogramowanie zakłóca ruch z hosta lokalnego.  
  
- W trakcie działania programu Visual Studio przestaje odpowiadać lub wystąpił problem z wydajnością. Jeśli problem występuje regularnie, można zbierać zrzuty programu Visual Studio (devenv.exe) i procesu roboczego (msvsmon.exe) i wysyłać je do firmy Microsoft. 
  
## <a name="see-also"></a>Zobacz też  
 [64-bitowe aplikacje](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Konfigurowanie programów dla 64-bitowych](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Obsługa programu Visual Studio IDE 64-bit](../ide/visual-studio-ide-64-bit-support.md)   
 [Korzystanie z plików zrzutu](../debugger/using-dump-files.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
