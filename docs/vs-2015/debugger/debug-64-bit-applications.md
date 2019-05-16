---
title: Debugowanie aplikacji 64-bitowych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2f67acff26d346b915f6b457fc0887f1d5f2ec3b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695905"
---
# <a name="debug-64-bit-applications"></a>Debugowanie aplikacji 64-bitowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [debugowania 64-bitowych aplikacji](https://docs.microsoft.com/visualstudio/debugger/debug-64-bit-applications) .  
  
Można debugować aplikację 64-bitowych, która jest uruchomiona na komputerze lokalnym lub na komputerze zdalnym.  
  
 Aby debugować aplikację 64-bitowych, która jest uruchomiona na komputerze zdalnym, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
 Debugowanie aplikacji 64-bitowych lokalnie, program Visual Studio używa procesu roboczego 64-bitowych (msvsmon.exe) do wykonywania operacji niskiego poziomu, których nie można wykonać w 32-bitowego procesu programu Visual Studio.  
  
 Debugowanie w trybie mieszanym nie jest obsługiwane dla procesów 64-bitowych, które używają .NET Framework w wersji 3.5 lub wcześniejszej.  
  
## <a name="debug-a-64-bit-application"></a>Debugowanie aplikacji 64-bitowych  
 Aby wypróbować, debugowanie aplikacji 64-bitowych:  
  
1. Utwórz rozwiązanie programu Visual Studio, na przykład aplikacja konsolowa C#.  
  
2. Ustaw konfigurację do 64-bitowego za pomocą programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie projektów pod kątem platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3. W tym momencie zostanie uruchomiony 64-bitowej wersji zdalnego debugera (msvsmon.exe). Działa tak długo, jak rozwiązanie przy użyciu konfiguracji 64-bitowych jest otwarte.  
  
4. Rozpocznij debugowanie. Powinny mieć taki sam sposób, podobnie jak w przypadku konfiguracji 32-bitowych. Jeśli występują błędy, zobacz poniżej sekcję Rozwiązywanie problemów.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Rozwiązywanie problemów z debugowaniem 64-bitowych  
 Może zostać wyświetlony błąd: "To operacja debugowania 64-bitowego trwa dłużej niż oczekiwano." W takim przypadku programu Visual Studio, który wysłał żądanie do 64-bitowej wersji msvsmon.exe i trzeba było poświęcić dużo czasu, w wyniku tego żądania, aby wrócić do tego.  
  
 Istnieją dwie główne przyczyny tego błędu:  
  
- Masz oprogramowanie zabezpieczeń sieciowe zainstalowane na komputerze, który spowodował stosu sieciowego być zawodne i została obniżona, pakiety przesyłane za pośrednictwem hosta lokalnego. Spróbuj wyłączyć całe oprogramowanie zabezpieczeń sieci i zobacz, jeśli to rozwiązuje to. Jeśli tak, zgłoś się z dostawcą oprogramowania zabezpieczeń sieci, oprogramowania uniemożliwiać ruch hosta lokalnego.  
  
- Zawieszanie się lub wydajności problem z programem Visual Studio zostały przekroczone. Jeśli ten problem występuje regularnie, można zbierać zrzuty programu Visual Studio (devenv.exe) i proces roboczy (msvsmon.exe) i wysyłać je do firmy Microsoft. 
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje 64-bitowe](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Konfigurowanie programów dla wersji 64-bitowych](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Obsługa 64-bitowego środowiska IDE programu Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Przy użyciu plików zrzutu](../debugger/using-dump-files.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
