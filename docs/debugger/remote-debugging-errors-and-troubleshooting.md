---
title: Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043346"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów

Mogą pochodzić między następujące błędy podczas próby debugowania zdalnego.

- [Błąd: Nie można automatycznie wkroczyć do serwera](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio (MSVSMON.EXE) prawdopodobnie nie jest uruchomiony na komputerze zdalnym.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Nie można połączyć z monitorem zdalnego debugowania programu Microsoft Visual Studio](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Błąd: Maszyna zdalna nie jest wyświetlana w oknie dialogowym połączeń zdalnych](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Uruchom zdalny debuger jako administrator

Mogą pochodzić różnych problemów, jeśli nie uruchomisz zdalny debuger jako administrator. Na przykład może zostać wyświetlony następujący błąd: "Visual Studio zdalny debuger (polecenia MSVSMON. Z rozszerzeniem EXE) ma niewystarczające uprawnienia do debugowania tego procesu". Jeśli używasz zdalnego debugera jako aplikacja (nie service), może zostać wyświetlony [innego konta użytkownika](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) błędu.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Podczas uruchamiania zdalnego debugera jako usługi

Podczas uruchamiania zdalnego debugera jako usługi s, zaleca się uruchamianie jej jako administrator z kilku powodów:

- Usługa zdalnego debugera umożliwia tylko nawiązywanie połączeń z administratorów, więc istnieją **nie** nowych zagrożeń bezpieczeństwa wprowadzone, uruchamiając go jako administrator.

- Może zablokować błędy, które obsługuje wynik po użytkownik programu Visual Studio ma dodatkowe uprawnienia, aby debugować proces niż sam debuger zdalny.

- Aby uprościć instalację i konfigurację zdalnego debugera.

Chociaż jest możliwe debugowanie bez uruchamiania debugera zdalnego jako administrator, kilka wymagań, aby działało prawidłowo, i często wymagają bardziej zaawansowanych kroki konfiguracji usługi.

- Konto używane na komputerze zdalnym musi mieć **Logowanie jako usługa** uprawnień. Zobacz opisane w sekcji "Dodawanie logowania jako usługa" w [nie można połączyć z powrotem](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) błędu.

- Konto musi mieć uprawnienia do debugowania procesu docelowego. Aby uzyskać te uprawnienia, możesz uruchomić zdalnego debugera z tego samego konta jako proces do debugowania. (Zamiast łatwiejsze jest do uruchomienia usługi jako administrator). 

- Konto musi być w stanie nawiązać połączenia zwrotnego (czyli uwierzytelnianie za pomocą) komputer Visual Studio za pośrednictwem sieci. W domenie łatwiej jest Połącz ponownie, jeśli debuger zdalny jest uruchomiony w ramach wbudowane konta systemu lokalnego lub usługi sieciowej lub konta domeny. Wbudowane konta mają podwyższony poziom uprawnień, które mogą stanowić zagrożenie dla bezpieczeństwa.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Podczas uruchamiania zdalnego debugera jako aplikacja (tryb normalny)

Jeśli próbujesz dołączyć do własnego procesu bez podniesionych uprawnień (np. normalne aplikacji), nie ma znaczenia, jeśli używasz zdalnego debugera jako administrator.

Chcesz uruchomić zdalny debuger jako administrator w kilku scenariuszach:

- Aby dołączyć do procesów uruchomionych jako inny użytkownik (np. gdy debugowanie usług IIS), lub

- Próbujesz uruchomić inny proces, a proces, który chcesz uruchomić, gdy administrator.

Możesz zrobić **nie** ma zostać uruchomiony z uprawnieniami administratora, jeśli chcesz uruchomić procesy, a proces, którego chcesz uruchomić powinien **nie** mieć uprawnienia administratora.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)