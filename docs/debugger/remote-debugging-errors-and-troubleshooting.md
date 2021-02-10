---
title: Błędy debugowania zdalnego i rozwiązywanie problemów | Microsoft Docs
description: Wyświetl linki do typowych błędów debugowania zdalnego w programie Visual Studio. Dowiedz się, jak uruchomić zdalny debuger jako administrator.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d046bfb0801229cd9f317ff2bcc8b715207ac2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934588"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów

Podczas próby debugowania zdalnego mogą wystąpić następujące błędy.

- [Błąd: Nie można automatycznie wkroczyć do serwera](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio (MSVSMON.EXE) prawdopodobnie nie jest uruchomiony na komputerze zdalnym.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Nie można nawiązać połączenia z Microsoft Visual Studio Monitor zdalnego debugowania](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Błąd: Komputer zdalny nie jest wyświetlany w oknie dialogowym połączeń zdalnych](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Uruchamianie debugera zdalnego jako administrator

Jeśli zdalny debuger nie zostanie uruchomiony jako administrator, mogą występować problemy. Na przykład może zostać wyświetlony następujący błąd: "zdalny debuger programu Visual Studio (MSVSMON.EXE) ma niewystarczające uprawnienia do debugowania tego procesu". W przypadku korzystania z zdalnego debugera jako aplikacji (a nie usługi) może zostać wyświetlony komunikat o błędzie [innego konta użytkownika](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) .

### <a name="when-running-the-remote-debugger-as-a-service"></a>Podczas uruchamiania zdalnego debugera jako usługi

W przypadku uruchamiania zdalnego debugera jako usługi s zalecamy uruchomienie go jako administrator z kilku powodów:

- Usługa zdalnego debugera zezwala tylko na połączenia od administratorów, więc **nie** wprowadzono nowych zagrożeń bezpieczeństwa przez uruchomienie go jako administrator.

- Może to uniemożliwić błędy, jeśli użytkownik programu Visual Studio ma więcej praw do debugowania procesu niż sam debuger zdalny.

- W celu uproszczenia instalacji i konfiguracji zdalnego debugera.

Chociaż jest możliwe debugowanie bez uruchamiania zdalnego debugera jako administrator, istnieje kilka wymagań, aby zapewnić to prawidłowe działanie i często wymagają bardziej zaawansowanych kroków konfiguracji usługi.

- Konto, którego używasz na komputerze zdalnym, musi mieć uprawnienie **Logowanie jako usługa** . Zapoznaj się z instrukcjami w sekcji "aby dodać Logowanie jako usługa" w artykule [nie można nawiązać połączenia z](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) błędem.

- Konto musi mieć uprawnienia do debugowania procesu docelowego. Aby uzyskać te prawa, należy uruchomić zdalny debuger w ramach tego samego konta, co proces, który ma być debugowany. (Łatwiejszym rozwiązaniem jest uruchomienie usługi jako administrator). 

- Konto musi mieć możliwość nawiązania połączenia z programem (czyli uwierzytelnianiem za pomocą programu) komputera z programem Visual Studio za pośrednictwem sieci. W domenie łatwiej jest połączyć się, jeśli zdalny debuger jest uruchomiony w ramach wbudowanego systemu lokalnego lub kont usługi sieciowej lub konta domeny. Wbudowane konta mają podwyższone uprawnienia zabezpieczeń, które mogą stanowić zagrożenie dla bezpieczeństwa.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Podczas uruchamiania debugera zdalnego jako aplikacji (tryb normalny)

Jeśli próbujesz dołączyć do własnego procesu bez podwyższonego poziomu uprawnień (takiego jak zwykła aplikacja), nie ma znaczenia, czy używasz zdalnego debugera jako administrator.

Chcesz uruchomić zdalny debuger jako administrator w kilku scenariuszach:

- Chcesz dołączyć do procesów uruchomionych jako inny użytkownik (na przykład podczas debugowania usług IIS) lub

- Próbujesz uruchomić inny proces, a proces, który chcesz uruchomić, jest administratorem.

**Nie** chcesz uruchamiać programu jako administrator, jeśli chcesz uruchamiać procesy, a proces, który chcesz uruchomić, **nie** powinien być administratorem.

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)