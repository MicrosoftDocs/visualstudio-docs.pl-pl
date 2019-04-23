---
title: Nie można nawiązać połączenia z programem Microsoft Visual Studio Monitor debugera zdalnego | Dokumentacja firmy Microsoft
ms.date: 08/24/2017
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
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
ms.openlocfilehash: e5c5f6d73f3606813fd9a1954cdc10bb562baf34
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070267"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
Ten komunikat może wystąpić, ponieważ monitor debugera zdalnego jest nie prawidłowo skonfigurowane na komputerze zdalnym lub maszynie zdalnej jest niedostępny z powodu problemów z siecią lub obecności zapory.

> [!IMPORTANT]
>  Jeśli uważasz, że ten komunikat został przesłany z powodu błędu w produkcie, [Zgłoś ten problem](../ide/how-to-report-a-problem-with-visual-studio.md) do programu Visual Studio. Jeśli potrzebujesz więcej pomocy, zobacz [Porozmawiaj z nami](../ide/talk-to-us.md) sposobów na kontakt z firmą Microsoft.

## <a name="specificerrors"></a>Co to jest komunikat szczegółowy komunikat o błędzie?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Jest ogólny komunikat. Zazwyczaj bardziej szczegółowy komunikat o błędzie, w której znajduje się w ciąg błędu i zidentyfikować przyczynę problemu lub Wyszukaj, aby dokładniej poprawki, może pomóc. Poniżej przedstawiono niektóre typowe komunikaty o błędach, które są dołączane do komunikatu o błędzie główne:

- [Debuger nie może połączyć się z komputerem zdalnym. Debuger nie może rozpoznać określonej nazwy komputera](#cannot_connect)
- [Żądanie połączenia zostało odrzucone przez debuger zdalny](#rejected)
- [Nieprawidłowy dostęp do lokalizacji w pamięci](#invalid_access)
- [Serwer nie jest z określoną nazwą, uruchomione na komputerze docelowym](#no_server)
- [Nazwa żądanego była prawidłowa, ale można odnaleźć żadnych danych żądanego typu](#valid_name)
- [Zdalny debuger programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](#cant_connect_back)
- [Odmowa dostępu](#access_denied)
- [Wystąpił błąd określonego pakietu zabezpieczeń](#security_package)

## <a name="cannot_connect"></a> Debuger nie może połączyć się z komputerem zdalnym. Debuger nie może rozpoznać określonej nazwy komputera

Spróbuj wykonać następujące kroki:

1. Upewnij się, że należy wprowadzić prawidłową nazwę komputera, a numer portu w **dołączyć do procesu** okno dialogowe lub we właściwościach projektu (do ustawiania właściwości, zobacz [te kroki](#server_incorrect)). Nazwa komputera musi mieć następujący format:

    `computername:port`

    > [!NOTE]
    > Numer portu musi być zgodny [numer_portu zdalny debuger](../debugger/remote-debugger-port-assignments.md), który *musi być uruchomiona* na komputerze docelowym.

2. Jeśli nazwa komputera nie działa, spróbuj użyć adresu IP i numer portu w zamian.

3. Upewnij się, że wersja zdalny debuger działający na maszynie docelowej pasuje do używanej wersji programu Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

    > [!TIP]
    > Jeśli jest podłączany do procesu i pomyślnego nawiązania połączenia, ale nie widzisz procesu, który ma, zaznacz **Pokaż procesy wszystkich pola wyboru Użytkownicy**. Spowoduje to wyświetlenie procesów jeśli nawiązano połączenie przy użyciu konta innego użytkownika.

4. Jeśli te kroki nie umożliwiają rozwiązania tego błędu, zobacz [Maszyna zdalna nie jest dostępny](#dns).

## <a name="rejected"></a> Żądanie połączenia zostało odrzucone przez debuger zdalny

W **dołączyć do procesu** okna dialogowego pole lub we właściwościach projektu upewnij się, że nazwy komputera zdalnego i numer portu pasuje numer portu i wyświetlane w oknie debugera zdalnego. Jeśli jest nieprawidłowy, napraw i spróbuj ponownie.

Jeśli te wartości są poprawne, a komunikat jest wspomniany **uwierzytelniania Windows** tryb, upewnij się, że debuger zdalny jest poprawny tryb uwierzytelniania (**Narzędzia > Opcje**).

## <a name="invalid_access"></a> Nieprawidłowy dostęp do lokalizacji w pamięci

Wystąpił błąd wewnętrzny. Uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="no_server"></a> Serwer nie jest z określoną nazwą, uruchomione na komputerze docelowym

Program Visual Studio nie może połączyć się ze zdalnym debugerem. Ten komunikat może wystąpić z kilku powodów:

- Zdalny debuger może być uruchomiony w ramach konta innego użytkownika. Zobacz [następujące kroki](#user_accounts)

- Numer portu jest zablokowany na zaporze. Upewnij się, że Zapora jest [nie blokuje Twoje żądanie](#firewall), zwłaszcza, jeśli używasz zapory innych firm.

- Wersja zdalnego debugera jest niezgodna z programu Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalnego debugowania](../debugger/remote-debugging.md)

## <a name="valid_name"></a> Nazwa żądanego była prawidłowa, ale można odnaleźć żadnych danych żądanego typu

Komputer zdalny istnieje, ale Visual Studio nie może nawiązać zdalnego debugera. Ten komunikat może wystąpić z kilku powodów:

- Problemy z usługą DNS uniemożliwia nawiązanie połączenia. Zobacz [te kroki](#dns).

- Zdalny debuger może być uruchomiony w ramach konta innego użytkownika. Postępuj zgodnie z [te kroki](#user_accounts).

- Numer portu jest zablokowany na zaporze. Upewnij się, że Zapora jest [nie blokuje Twoje żądanie](#firewall), zwłaszcza, jeśli używasz zapory innych firm.

- Wersja zdalnego debugera jest niezgodna z programu Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a> Zdalny debuger programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem

Zdalny debuger może być uruchomiony w ramach konta innego użytkownika. Zdalny debuger, otwórz **Narzędzia > uprawnienia** można dodać użytkownika do zdalnego debugera uprawnień. Aby uzyskać więcej informacji, zobacz [debuger zdalny jest uruchomiony w ramach konta innego użytkownika](#user_accounts).

Jeśli komunikat o błędzie zawiera również zapory, zapora na komputerze lokalnym może blokować komunikację z komputera zdalnego, wróć do programu Visual Studio. Zobacz [te kroki](#firewall).

## <a name="access_denied"></a> Odmowa dostępu

Może zostać wyświetlony ten błąd, jeśli zostanie podjęta próba debugowania na komputerze zdalnym 64-bitowym na komputerze 32-bitowych (nieobsługiwane).

## <a name="security_package"></a> Wystąpił błąd określonego pakietu zabezpieczeń

Może to być problem starszych specyficzne dla Windows XP i Windows 7. Zobacz ten [informacji](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Przyczyny i zalecenia

### <a name="dns"></a> Maszyna zdalna nie jest dostępny

Jeśli nie możesz się połączyć przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP zamiast tego. Możesz użyć `ipconfig` w wierszu polecenia na komputerze zdalnym, aby uzyskać adres IPv4. Jeśli używasz pliku HOSTS, sprawdź, czy jest poprawnie skonfigurowana.

Jeśli ono zawiedzie, sprawdź, czy komputer zdalny jest dostępny w sieci ([ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) maszyny zdalnej). Debugowanie zdalne przez Internet nie jest obsługiwany, chyba że w niektórych scenariuszach Microsoft Azure.

### <a name="server_incorrect"></a> Nazwa serwera jest niepoprawna lub oprogramowania innych firm nie zakłócają jest debugera zdalnego

W programie Visual Studio Spójrz na właściwości projektu i upewnij się, że nazwa serwera jest prawidłowa. W tematach [C# i Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) i [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). W technologii ASP.NET, należy otworzyć **właściwości / Web / serwerów** lub **właściwości / Debug** w zależności od typu projektu.

> [!NOTE]
> Dołączając do procesu, nie są używane ustawienia zdalne we właściwościach projektu.

Jeśli nazwa serwera jest poprawna, oprogramowanie antywirusowe lub zapory innych firm może blokować zdalnego debugera. Podczas lokalnego debugowania można to zrobić, ponieważ program Visual Studio jest 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania 64-bitowych aplikacji. 32-bitowych i 64-bitowych procesów komunikacji za pośrednictwem sieci lokalnej na komputerze lokalnym. Żaden ruch sieciowy pozostawia komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innych firm mogą blokować komunikacji.

### <a name="user_accounts"></a> Debuger zdalny jest uruchomiony w ramach konta innego użytkownika

Zdalny debuger domyślnie przyjmuje tylko połączenia od użytkownika, który uruchomił zdalny debuger i członkowie grupy Administratorzy. Dodatkowym użytkownikom trzeba jawnie udzielić uprawnień.

Problem można rozwiązać w jednym z następujących sposobów:

- Dodaj użytkownika programu Visual Studio do zdalnego debugera uprawnień (w oknie zdalnego debugera, wybierz **Narzędzia > uprawnienia**).

- Na komputerze zdalnym Uruchom ponownie debuger zdalny w ramach tego samego konta użytkownika i hasło, którego używasz na komputerze programu Visual Studio.

    > [!NOTE]
    > Jeśli używasz zdalnego debugera na serwerze zdalnym, kliknij prawym przyciskiem myszy aplikację zdalny debuger i wybierz polecenie **Uruchom jako administrator** (lub, można uruchomić zdalnego debugera jako usługi). Jeśli nie używasz go na serwerze zdalnym, wystarczy ją uruchomić normalnie.

- Zdalny debuger można uruchomić z wiersza polecenia za pomocą **/ allow \<username >** parametru: `msvsmon /allow <username@computer>`.

- Alternatywnie możesz zezwolić użytkownikowi przeprowadzać debugowanie zdalne. W oknie zdalnego debugera, przejdź do **Narzędzia > Opcje** okna dialogowego. Po wybraniu **bez uwierzytelniania**, można sprawdzić **Zezwalaj dowolnemu użytkownikowi na debugowanie**. Należy jednak Użyj tej opcji tylko wtedy, gdy inne opcje się nie powieść lub jeśli korzystasz z sieci prywatnej.

### <a name="firewall"></a> Zapora na zdalnym komputerze nie zezwala na połączenia przychodzące do zdalnego debugera
 Zapora na komputerze programu Visual Studio, a zapora na zdalnym komputerze musi być skonfigurowany do zezwalania na komunikację między Visual Studio i zdalnym debugerem. Aby uzyskać informacji o portach używa zdalnego debugera, zobacz [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory Windows, zobacz [skonfigurować zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie pasuje do wersji programu Visual Studio
 Wersję programu Visual Studio, które działają lokalnie musi być zgodna z wersją monitor debugera zdalnego działa na komputerze zdalnym. Aby rozwiązać ten problem, należy pobrać i zainstalować zgodną wersję monitor debugera zdalnego. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Maszyny lokalne i zdalne mają tryby uwierzytelniania innego
 Maszyn lokalnych i zdalnych muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny będą używać trybu uwierzytelniania. Można zmienić tryb uwierzytelniania. W oknie zdalnego debugera, przejdź do **Narzędzia > Opcje** okno dialogowe.

 Aby uzyskać więcej informacji na temat trybów uwierzytelniana, zobacz [omówienie uwierzytelniania Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia
 Program antywirusowy Windows zezwala na połączenia zdalnego debugera, ale niektóre programy antywirusowe innej firmy mogą je zablokować. Sprawdź w dokumentacji oprogramowanie antywirusowe dowiedzieć się, jak umożliwić tych połączeń.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokuje komunikację między komputerem zdalnym i programu Visual Studio
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci Windows zobacz [ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęty, aby zapewnić obsługę zdalnego debugowania
 Może być konieczne przeprowadzać debugowanie zdalne w innym czasie lub Zmień harmonogram pracy w sieci inny czas.

## <a name="more-help"></a>Więcej pomocy
 Aby uzyskać pomoc w bardziej zdalnego debugera, otwórz stronę pomocy zdalny debuger (**Pomoc > użycie** w zdalnym debugerze).

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)
