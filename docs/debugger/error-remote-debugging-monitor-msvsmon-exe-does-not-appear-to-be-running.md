---
title: 'Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio (MSVSMON.EXE) prawdopodobnie nie jest uruchomiony na komputerze zdalnym.'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 40210832f06a328ec2fc785a2543eb3bbce9f6ba
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867997"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Błąd: Monitor zdalnego debugowania programu Microsoft Visual Studio (MSVSMON.EXE) prawdopodobnie nie jest uruchomiony na komputerze zdalnym.
Ten komunikat o błędzie oznacza, że program Visual Studio nie można odnaleźć poprawne wystąpienie programu Visual Studio Monitor zdalnego debugowania na komputerze zdalnym. Visual Studio Monitor zdalnego debugowania musi być zainstalowany dla zdalnego debugowania do pracy. Aby uzyskać informacje dotyczące pobierania i konfigurowania zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

> [!IMPORTANT]
> Jeśli uważasz, że ten komunikat pojawił się z powodu błędu w produkcie, [Zgłoś ten problem w programie Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md). Jeśli potrzebujesz więcej pomocy, zobacz [Porozmawiaj z nami](../ide/talk-to-us.md) sposobów na kontakt z firmą Microsoft.

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Został wyświetlony komunikat, gdy został I debugowania w programie Visual Studio 2010 lub starszy
 Wersja programu Visual Studio, którego używasz w przypadku programu Visual Studio 2010 lub starszy, ten błąd może również występować Jeśli udostępnianie plików i drukarek nie jest włączona. Aby dowiedzieć się więcej na temat tego problemu, można znaleźć programu Visual Studio 2010 w niniejszej dokumentacji: [Błąd: Microsoft Visual Studio Monitor debugera zdalnego (polecenia MSVSMON. Z rozszerzeniem EXE) nie jest uruchomiony na komputerze zdalnym. — Program visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Został wyświetlony komunikat, gdy został I debugowanie lokalnie
 Jeśli otrzymujesz ten komunikat, gdy debugujesz lokalnie, oprogramowanie antywirusowe lub zapory innych firm może być stronę. Visual Studio to 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania 64-bitowych aplikacji. Dwa procesy komunikacji za pośrednictwem sieci lokalnej na komputerze lokalnym. Żaden ruch opuszcza komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innych firm mogą blokować komunikacji.

 W poniższych sekcjach wymieniono niektóre inne przyczyny, dlaczego użytkownik może stają się coraz ten komunikat i co można zrobić, aby rozwiązać ten problem.

## <a name="the-remote-machine-is-not-reachable"></a>Maszyna zdalna nie jest dostępny
 Spróbuj [ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) maszyny zdalnej. Jeśli go nie odpowiada na polecenie ping, narzędzi zdalnych nie będzie można połączyć w jedną. Spróbuj ponownie uruchamiając komputer zdalny, a w przeciwnym razie upewniając się, że została poprawnie skonfigurowana w sieci.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie pasuje do wersji programu Visual Studio
 Wersję programu Visual Studio, które działają lokalnie musi być zgodna z wersją monitor debugera zdalnego działa na komputerze zdalnym. Aby rozwiązać ten problem, należy pobrać i zainstalować zgodną wersję monitor debugera zdalnego. Przejdź do [Centrum pobierania](http://www.microsoft.com/en-us/download) można znaleźć właściwą wersję zdalnego debugera.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Maszyny lokalne i zdalne mają tryby uwierzytelniania innego
 Maszyn lokalnych i zdalnych muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny będą używać trybu uwierzytelniania. Aby uzyskać więcej informacji na temat trybów uwierzytelniana, zobacz [omówienie uwierzytelniania Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Debuger zdalny jest uruchomiony w ramach konta innego użytkownika
 Problem można rozwiązać w jednym z następujących sposobów:

-   Można zatrzymać debuger zdalny i uruchom go ponownie przy użyciu konta, którego używasz na komputerze lokalnym.

-   Zdalny debuger można uruchomić z wiersza polecenia za pomocą **/ allow \<username >** parametru: `msvsmon /allow <username@computer>`

-   Można dodać użytkownika do zdalnego debugera uprawnień (w oknie debugera zdalnego **Narzędzia > uprawnienia**).

-   Jeśli nie możesz użyć metody w poprzednich krokach, możesz zezwolić użytkownikowi przeprowadzać debugowanie zdalne. W oknie zdalnego debugera, przejdź do **Narzędzia > Opcje** okna dialogowego. Po wybraniu **bez uwierzytelniania**, można sprawdzić **Zezwalaj dowolnemu użytkownikowi na debugowanie**. Jednak należy używać tej opcji tylko wtedy, gdy możesz nie mieć wyboru, czy znajdują się w sieci prywatnej.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Zapora na zdalnym komputerze nie zezwala na połączenia przychodzące do zdalnego debugera
 Zapora na komputerze programu Visual Studio, a zapora na zdalnym komputerze musi być skonfigurowany do zezwalania na komunikację między Visual Studio i zdalnym debugerem. Aby uzyskać informacji o portach używa zdalnego debugera, zobacz [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory Windows, zobacz [skonfigurować zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia
 Program antywirusowy Windows zezwala na połączenia zdalnego debugera, ale niektóre programy antywirusowe innej firmy mogą je zablokować. Sprawdź w dokumentacji oprogramowanie antywirusowe dowiedzieć się, jak umożliwić tych połączeń.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokuje komunikację między komputerem zdalnym i programu Visual Studio
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci Windows zobacz [ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęty, aby zapewnić obsługę zdalnego debugowania
 Może być konieczne przeprowadzać debugowanie zdalne w innym czasie lub Zmień harmonogram pracy w sieci inny czas.

## <a name="more-help"></a>Więcej pomocy
 Aby Pomoc zdalny debuger, łącznie z przełączników wiersza polecenia, kliknij przycisk **Pomoc > użycie** w oknie debugera zdalnego. Jeśli nie masz otwarty zostanie wyświetlona strona sieci web, kopiując następujący wiersz do **Eksploratora plików** okna. (Należy zastąpić \<katalogu instalacyjnego programu Visual Studio > z lokalizacji instalacji programu Visual Studio.)

 res: / /*\<katalogu instalacyjnego programu Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Zobacz też
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
