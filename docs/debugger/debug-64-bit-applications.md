---
title: Debuguj 64-bitowe aplikacje | Microsoft Docs
description: Dowiedz się, jak debugować aplikację 64-bitową za pomocą programu Visual Studio. Istnieją wskazówki dotyczące rozwiązywania nieoczekiwanych opóźnień debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18ea2ade8ed87bfc58280bf5b2dc45c633eb2055
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857600"
---
# <a name="debug-64-bit-applications"></a>Debugowanie aplikacji 64-bitowych
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

- W trakcie działania programu Visual Studio przestaje odpowiadać lub Wystąpił inny problem z wydajnością. Jeśli problem występuje regularnie, można zbierać zrzuty programu Visual Studio (devenv.exe) i procesu roboczego (msvsmon.exe) i wysyłać je do firmy Microsoft. Aby uzyskać informacje o raportowaniu problemu, zobacz artykuł [Jak zgłosić problem w programie Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Aplikacje 64-bitowe](/dotnet/framework/64-bit-apps)
- [Konfigurowanie programów dla 64-bitowych](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Obsługa programu Visual Studio IDE 64-bit](../ide/visual-studio-ide-64-bit-support.md)
- [Używanie plików zrzutów](../debugger/using-dump-files.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)