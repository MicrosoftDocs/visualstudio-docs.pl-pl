---
title: Błędy zdalnego debugowania i rozwiązywanie problemów | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302092"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów

Podczas próby zdalnego debugowania można natknąć się na następujące błędy.

- [Błąd: Nie można automatycznie wkroczyć do serwera](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio (MSVSMON.EXE) prawdopodobnie nie jest uruchomiony na komputerze zdalnym.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Błąd: Komputer zdalny nie jest wyświetlany w oknie dialogowym połączeń zdalnych](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Uruchamianie debugera zdalnego jako administratora

Jeśli debuger zdalny nie zostanie uruchomiony jako administrator, mogą wystąpić problemy. Na przykład może zostać wyświetlony następujący błąd: "Debuger zdalny programu Visual Studio (MSVSMON. EXE) nie ma wystarczających uprawnień do debugowania tego procesu." Jeśli korzystasz z debugera zdalnego jako aplikacji (nie usługi), może zostać wyświetlony błąd [innego konta użytkownika.](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)

### <a name="when-running-the-remote-debugger-as-a-service"></a>Podczas uruchamiania zdalnego debugera jako usługi

Podczas uruchamiania zdalnego debugera jako usługi s zalecamy uruchomienie go jako administratora z kilku powodów:

- Usługa zdalnego debugera zezwala tylko na połączenia od administratorów, więc **nie ma żadnych** nowych zagrożeń bezpieczeństwa wprowadzonych przez uruchomienie go jako administratora.

- Można zapobiec błędom, które wynik, gdy użytkownik programu Visual Studio ma więcej praw do debugowania procesu niż zdalnego debugera sam nie.

- Aby uprościć konfigurację i konfigurację zdalnego debugera.

Chociaż jest możliwe do debugowania bez uruchamiania debugera zdalnego jako administrator, istnieje kilka wymagań, aby to działało poprawnie i często wymagają bardziej zaawansowanych kroków konfiguracji usługi.

- Konto używane na komputerze zdalnym musi mieć **uprawnienia logowania jako usługi.** Zobacz kroki w obszarze "Aby dodać logowanie jako usługę" w nie [można połączyć z powrotem](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) błąd artykułu.

- Konto musi mieć prawa do debugowania procesu docelowego. Aby uzyskać te prawa, należy uruchomić debuger zdalny przy tym samym koncie co proces, który ma zostać debugowany. (Łatwiejszą alternatywą jest uruchomienie usługi jako administratora). 

- Konto musi mieć możliwość łączenia się z komputerem programu Visual Studio za pośrednictwem sieci(tj. uwierzytelnić się za pomocą) komputera programu Visual Studio. W domenie łatwiej jest połączyć się z powrotem, jeśli debuger zdalny jest uruchomiony przy wbudowanych kontach systemu lokalnego lub usługi sieciowej lub konta domeny. Wbudowane konta mają podwyższone uprawnienia zabezpieczeń, które mogą stanowić zagrożenie bezpieczeństwa.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Podczas uruchamiania zdalnego debugera jako aplikacji (tryb normalny)

Jeśli próbujesz dołączyć do własnego procesu nie podwyższonego poziomu (na przykład normalnej aplikacji), nie ma znaczenia, czy korzystasz z debugera zdalnego jako administrator.

Debuger zdalny ma być uruchamiany jako administrator w kilku scenariuszach:

- Chcesz dołączyć do procesów uruchomionych jako inny użytkownik (np. podczas debugowania usługi IIS) lub

- Próbujesz uruchomić inny proces, a proces, który chcesz uruchomić, jest administratorem.

**Nie** chcesz uruchamiać jako administrator, jeśli chcesz uruchomić procesy, a proces, który chcesz uruchomić, **nie** powinien być administratorem.

## <a name="see-also"></a>Zobacz też
- [Zdalne debugowanie](../debugger/remote-debugging.md)