---
title: Debugowanie aplikacji 64-bitowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f79bd9c0f2bbf2ab3156f5bc49100c9c8aee536
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947364"
---
# <a name="debug-64-bit-applications"></a>Debugowanie aplikacji 64-bitowych
Można debugować aplikację 64-bitowych, która jest uruchomiona na komputerze lokalnym lub na komputerze zdalnym.  
  
 Aby debugować aplikację 64-bitowych, która jest uruchomiona na komputerze zdalnym, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
 Debugowanie aplikacji 64-bitowych lokalnie, program Visual Studio używa procesu roboczego 64-bitowych (msvsmon.exe) do wykonywania operacji niskiego poziomu, których nie można wykonać w 32-bitowego procesu programu Visual Studio.  
  
 Debugowanie w trybie mieszanym nie jest obsługiwane dla procesów 64-bitowych, które używają .NET Framework w wersji 3.5 lub wcześniejszej.  
  
## <a name="debug-a-64-bit-application"></a>Debugowanie aplikacji 64-bitowych  
 Aby wypróbować, debugowanie aplikacji 64-bitowych:  
  
1.  Utwórz rozwiązanie programu Visual Studio, na przykład aplikacja konsolowa C#.  
  
2.  Ustaw konfigurację do 64-bitowego za pomocą programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie projektów pod kątem platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  W tym momencie zostanie uruchomiony 64-bitowej wersji zdalnego debugera (msvsmon.exe). Działa tak długo, jak rozwiązanie przy użyciu konfiguracji 64-bitowych jest otwarte.  
  
4.  Rozpocznij debugowanie. Powinny mieć taki sam sposób, podobnie jak w przypadku konfiguracji 32-bitowych. Jeśli występują błędy, zobacz poniżej sekcję Rozwiązywanie problemów.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Rozwiązywanie problemów z debugowaniem 64-bitowych  
 Może zostać wyświetlony błąd: "To operacja debugowania 64-bitowego trwa dłużej niż oczekiwano." W takim przypadku programu Visual Studio, który wysłał żądanie do 64-bitowej wersji msvsmon.exe i trzeba było poświęcić dużo czasu, w wyniku tego żądania, aby wrócić do tego.  
  
 Istnieją dwie główne przyczyny tego błędu:  
  
-   Masz oprogramowanie zabezpieczeń sieciowe zainstalowane na komputerze, który spowodował stosu sieciowego być zawodne i została obniżona, pakiety przesyłane za pośrednictwem hosta lokalnego. Spróbuj wyłączyć całe oprogramowanie zabezpieczeń sieci i zobacz, jeśli to rozwiązuje to. Jeśli tak, zgłoś się z dostawcą oprogramowania zabezpieczeń sieci, oprogramowania uniemożliwiać ruch hosta lokalnego.  
  
-   Zawieszanie się lub wydajności problem z programem Visual Studio zostały przekroczone. Jeśli ten problem występuje regularnie, można zbierać zrzuty programu Visual Studio (devenv.exe) i proces roboczy (msvsmon.exe) i wysyłać je do firmy Microsoft. Aby uzyskać informacji o raportowaniu problem, zobacz [jak zgłosić Problem z programem Visual Studio](../ide/How-to-Report-a-Problem-with-Visual-Studio-2017.md).
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje 64-bitowe](https://docs.microsoft.com/dotnet/framework/64-bit-apps)   
 [Konfigurowanie programów dla wersji 64-bitowych](/cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Obsługa 64-bitowego środowiska IDE programu Visual Studio](../ide/visual-studio-ide-64-bit-support.md)   
 [Przy użyciu plików zrzutu](../debugger/using-dump-files.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)