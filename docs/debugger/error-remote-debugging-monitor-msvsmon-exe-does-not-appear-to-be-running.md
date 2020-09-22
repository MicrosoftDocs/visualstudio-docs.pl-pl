---
title: Monitor zdalnego debugowania programu Microsoft Visual Studio (MSVSMON.EXE) prawdopodobnie nie jest uruchomiony na komputerze zdalnym.
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe0fc33c142c1bc70655817f833ae7c80fc628e7
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852579"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Błąd: Monitor debugera zdalnego Microsoft Visual (MSVSMON.EXE) zdaje się nie być uruchomiony na komputerze zdalnym.
Ten komunikat o błędzie oznacza, że program Visual Studio nie może znaleźć poprawnego wystąpienia Monitor zdalnego debugowania programu Visual Studio na komputerze zdalnym. Aby debugowanie zdalne działało, należy zainstalować Monitor zdalnego debugowania programu Visual Studio. Aby uzyskać informacje o pobieraniu i konfigurowaniu zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

> [!IMPORTANT]
> Jeśli uważasz, że ta wiadomość została odebrana z powodu błędu produktu, [Zgłoś ten problem w programie Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md). Jeśli potrzebujesz więcej pomocy, skontaktuj się [z nami](../ide/feedback-options.md) , aby dowiedzieć się, jak skontaktować się z firmą Microsoft.

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Ten komunikat został wyświetlony podczas debugowania w programie Visual Studio 2010 lub starszym
 Jeśli używana wersja programu Visual Studio jest w wersji Visual Studio 2010 lub starszej, można również otrzymać ten błąd, jeśli udostępnianie plików i drukarek nie jest włączone. Aby dowiedzieć się więcej o tym problemie, zapoznaj się z wersją programu Visual Studio 2010 w tej dokumentacji: [błąd: Microsoft Visual Studio Monitor zdalnego debugowania (MSVSMON.EXE) nie jest uruchomiona na komputerze zdalnym. — Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Mam ten komunikat podczas debugowania lokalnego
 Jeśli ten komunikat jest wyświetlany podczas debugowania lokalnego, oprogramowanie antywirusowe lub zapora innej firmy może być polecenia Blame. Program Visual Studio jest aplikacją 32-bitową, więc używa wersji 64-bitowej zdalnego debugera do debugowania aplikacji 64-bitowych. Dwa procesy komunikują się przy użyciu sieci lokalnej na komputerze lokalnym. Żaden ruch nie opuszcza komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innej firmy może blokować komunikację.

 W poniższych sekcjach wymieniono niektóre z tych powodów, dla których może zostać wyświetlony ten komunikat i co można zrobić, aby rozwiązać ten problem.

## <a name="the-remote-machine-is-not-reachable"></a>Maszyna zdalna jest nieosiągalna
 Spróbuj [wysłać polecenie ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) do komputera zdalnego. Jeśli nie odpowiada na polecenie ping, narzędzia zdalne nie będą mogły nawiązywać połączenia. Spróbuj ponownie uruchomić maszynę zdalną i w inny sposób upewnij się, że jest prawidłowo skonfigurowana w sieci.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie jest zgodna z wersją programu Visual Studio
 Wersja programu Visual Studio, która jest uruchamiana lokalnie, musi być zgodna z wersją monitora debugowania zdalnego, który jest uruchomiony na komputerze zdalnym. Aby rozwiązać ten problem, Pobierz i zainstaluj zgodną wersję monitora zdalnego debugowania. Przejdź do [Centrum pobierania](https://www.microsoft.com/download) , aby znaleźć odpowiednią wersję zdalnego debugera.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Komputery lokalne i zdalne mają różne tryby uwierzytelniania
 Maszyny lokalne i zdalne muszą korzystać z tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny używają tego samego trybu uwierzytelniania. Aby uzyskać więcej informacji na temat trybów uwierzytelniania, zobacz [Omówienie uwierzytelniania systemu Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Zdalny debuger działa na innym koncie użytkownika
 Można to rozwiązać w jeden z następujących sposobów:

- Można zatrzymać zdalny debuger i uruchomić go ponownie przy użyciu konta używanego na komputerze lokalnym.

- Zdalny debuger można uruchomić z wiersza polecenia z parametrem **/Allow \<username> ** :`msvsmon /allow <username@computer>`

- Możesz dodać użytkownika do uprawnień zdalnego debugera (w oknie zdalny debuger, **narzędzia > uprawnienia**).

- Jeśli nie można użyć metod w powyższych krokach, można zezwolić każdemu użytkownikowi na zdalne debugowanie. W oknie Debuger zdalny przejdź do okna dialogowego **narzędzia > opcje** . W przypadku wybrania opcji   **Brak uwierzytelniania**można zaznaczyć pole wyboru **Zezwalaj każdemu użytkownikowi na Debugowanie**. Należy jednak użyć tej opcji tylko wtedy, gdy nie masz wyboru lub jeśli jesteś w sieci prywatnej.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Zapora na maszynie zdalnej nie zezwala na połączenia przychodzące ze zdalnym debugerem
 Zapora na komputerze z programem Visual Studio i Zapora na maszynie zdalnej musi być skonfigurowana w taki sposób, aby zezwalała na komunikację między programem Visual Studio i zdalnym debugerem. Informacje o portach, które są używane przez zdalny debuger, można znaleźć w temacie [przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory systemu Windows, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia
 Oprogramowanie antywirusowe systemu Windows umożliwia połączenia zdalnego debugera, ale niektóre oprogramowanie antywirusowe innej firmy może je zablokować. Zapoznaj się z dokumentacją oprogramowania antywirusowego, aby dowiedzieć się, jak zezwolić na te połączenia.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokują komunikację między maszyną zdalną a programem Visual Studio
 Sprawdź zabezpieczenia sieci, aby upewnić się, że nie blokuje ona komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci systemu Windows, zobacz [Ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęta, aby obsługiwać debugowanie zdalne
 Może być konieczne przeprowadzenie debugowania zdalnego w innym czasie lub ponowne zaplanowanie pracy w sieci przez inny czas.

## <a name="more-help"></a>Więcej pomocy
 Aby uzyskać więcej pomocy dotyczącej zdalnego debugera, w tym przełączników wiersza polecenia, kliknij przycisk **pomoc > użycie** w oknie Debuger zdalny. Jeśli go nie masz, możesz zobaczyć stronę sieci Web, kopiując Poniższy wiersz do okna  **Eksploratora plików** . (Należy zamienić na \<Visual Studio installation directory> lokalizację instalacji programu Visual Studio).

 res:// *\<Visual Studio installation directory>* \Common7\IDE\Remote% 20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Zobacz także
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
