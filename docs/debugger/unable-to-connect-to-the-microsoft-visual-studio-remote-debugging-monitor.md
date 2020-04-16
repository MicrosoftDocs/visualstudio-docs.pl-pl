---
title: Nie można połączyć się z Monitorem zdalnego debugowania programu Microsoft Visual Studio | Dokumenty firmy Microsoft
ms.date: 04/14/2020
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
ms.openlocfilehash: d6173d6b3525a1bd723bc859d34b889b3796d295
ms.sourcegitcommit: c3b92a9912a5816f16c6059d1738dbc833851346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81397379"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
Ten komunikat może wystąpić, ponieważ monitor zdalnego debugowania nie jest poprawnie skonfigurowany na komputerze zdalnym lub komputer zdalny jest niedostępny z powodu problemów z siecią lub obecności zapory.

> [!IMPORTANT]
> Jeśli uważasz, że otrzymałeś ten komunikat z powodu błędu produktu, [zgłoś ten problem](../ide/how-to-report-a-problem-with-visual-studio.md) do programu Visual Studio. Jeśli potrzebujesz więcej pomocy, zobacz [Porozmawiaj z nami, aby](../ide/feedback-options.md) uzyskać sposoby kontaktu z firmą Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Co to jest szczegółowy komunikat o błędzie?

Wiadomość `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` jest ogólna. Zazwyczaj bardziej szczegółowy komunikat znajduje się w ciągu błędu, a to może pomóc zidentyfikować przyczynę problemu lub wyszukać bardziej dokładną poprawkę. Oto kilka z bardziej typowych komunikatów o błędach, które są dołączane do głównego komunikatu o błędzie:

- [Debuger nie może połączyć się z komputerem zdalnym. Debuger nie może rozpoznać określonej nazwy komputera](#cannot_connect)
- [Żądanie połączenia zostało odrzucone przez debuger zdalny](#rejected)
- [Połączenie ze zdalnym punktem końcowym zostało zakończone](#connection_terminated)
- [Nieprawidłowy dostęp do lokalizacji pamięci](#invalid_access)
- [Brak serwera o określonej nazwie uruchomionej na komputerze zdalnym](#no_server)
- [Żądana nazwa była prawidłowa, ale nie znaleziono żadnych danych żądanego typu](#valid_name)
- [Debuger zdalny programu Visual Studio na komputerze docelowym nie może połączyć się z powrotem do tego komputera](#cant_connect_back)
- [Odmowa dostępu](#access_denied)
- [Wystąpił błąd specyficzny dla pakietu zabezpieczeń](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>Debuger nie może połączyć się z komputerem zdalnym. Debuger nie może rozpoznać określonej nazwy komputera

Wypróbuj następujące rozwiązania:

1. Upewnij się, że w oknie dialogowym **Dołączanie do procesu** lub we właściwościach projektu (Aby ustawić właściwości, wykonaj [następujące kroki,](#server_incorrect)należy wprowadzić prawidłową nazwę komputera i numer portu). Nazwa komputera musi być następująca:

    `computername:port`

    > [!NOTE]
    > Numer portu musi być zgodny [z numerem portu zdalnego debugera,](../debugger/remote-debugger-port-assignments.md)który *musi być uruchomiony* na komputerze docelowym.

2. Jeśli nazwa komputera nie działa, spróbuj użyć adresu IP i numeru portu.

3. Upewnij się, że wersja zdalnego debugera uruchomionego na komputerze docelowym jest zgodna z wersją programu Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [Debugowanie zdalne](../debugger/remote-debugging.md).

    > [!TIP]
    > Jeśli dołączasz do procesu i łączysz się pomyślnie, ale nie widzisz odpowiedniego procesu, zaznacz **pole wyboru Pokaż procesy spośród wszystkich użytkowników**. Spowoduje to wyświetlenie procesów, jeśli użytkownik jest połączony z innym kontem użytkownika.

4. Jeśli te kroki nie rozwiążą tego błędu, zobacz [Komputer zdalny jest niedoścignialny](#dns).

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>Żądanie połączenia zostało odrzucone przez debuger zdalny

W oknie dialogowym **Dołączanie do procesu** lub we właściwościach projektu upewnij się, że nazwa komputera zdalnego i numer portu są zgodne z nazwą i numerem portu wyświetlanym w oknie zdalnego debugera. Jeśli jest niepoprawna, napraw i spróbuj ponownie.

Jeśli te wartości są poprawne, a komunikat wspomina o trybie **uwierzytelniania systemu Windows,** sprawdź, czy debuger zdalny jest w prawidłowym trybie uwierzytelniania (**Narzędzia > Opcje**).

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>Połączenie ze zdalnym punktem końcowym zostało zakończone

Jeśli debugujesz aplikację usługi Azure App Service, spróbuj użyć polecenia [Dołącz debuger](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) z Eksploratora chmury lub Eksploratora serwera zamiast **dołączania do procesu**.

Jeśli do debugowania używasz funkcji Dołącz do **procesu:**

- W oknie dialogowym **Dołączanie do procesu** lub we właściwościach projektu upewnij się, że nazwa komputera zdalnego i numer portu są zgodne z nazwą i numerem portu wyświetlanym w oknie zdalnego debugera. Jeśli jest niepoprawna, napraw i spróbuj ponownie.

- Jeśli próbujesz połączyć się przy użyciu nazwy hosta, spróbuj zamiast tego użyć adresu IP.

- Sprawdź dziennik aplikacji na serwerze (Podgląd zdarzeń w systemie Windows), aby uzyskać bardziej szczegółowe informacje ułatwiające rozwiązanie problemu.

- W przeciwnym razie spróbuj ponownie uruchomić program Visual Studio z uprawnieniami administratora, a następnie spróbuj ponownie.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>Nieprawidłowy dostęp do lokalizacji pamięci

Wystąpił błąd wewnętrzny. Uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>Brak serwera o określonej nazwie uruchomionej na komputerze zdalnym

Visual Studio nie może połączyć się z debugerem zdalnym. Ten komunikat może wystąpić z kilku powodów:

- Debuger zdalny może być uruchomiony w ramach innego konta użytkownika. Zobacz [te kroki](#user_accounts)

- Port jest zablokowany na zaporze. Upewnij się, że zapora [nie blokuje żądania,](#firewall)zwłaszcza jeśli używasz zapory innej firmy.

- Wersja zdalnego debugera nie jest zgodna z programem Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [Debugowanie zdalne](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>Żądana nazwa była prawidłowa, ale nie znaleziono żadnych danych żądanego typu

Komputer zdalny istnieje, ale program Visual Studio nie może połączyć się z debugerem zdalnym. Ten komunikat może wystąpić z kilku powodów:

- Problem z systemem DNS uniemożliwia połączenie. Zobacz [te kroki](#dns).

- Debuger zdalny może być uruchomiony w ramach innego konta użytkownika. Wykonaj [następujące kroki](#user_accounts).

- Port jest zablokowany na zaporze. Upewnij się, że zapora [nie blokuje żądania,](#firewall)zwłaszcza jeśli używasz zapory innej firmy.

- Wersja zdalnego debugera nie jest zgodna z programem Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [Debugowanie zdalne](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>Debuger zdalny programu Visual Studio na komputerze docelowym nie może połączyć się z powrotem do tego komputera

Debuger zdalny może być uruchomiony w ramach innego konta użytkownika. W debugerze zdalnym otwórz **narzędzia > uprawnienia,** aby dodać użytkownika do uprawnień zdalnego debugera. Aby uzyskać więcej informacji, zobacz [Debuger zdalny działa na innym koncie użytkownika](#user_accounts).

Jeśli komunikat o błędzie wspomina również o zaporze, zapora na komputerze lokalnym może uniemożliwiać komunikację z komputera zdalnego z powrotem do programu Visual Studio. Zobacz [te kroki](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a>Odmowa dostępu

Ten błąd może wystąpić podczas próby debugowania na 64-bitowym komputerze zdalnym z komputera 32-bitowego (nieobjętego).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>Wystąpił błąd specyficzny dla pakietu zabezpieczeń

Może to być starszy problem specyficzny dla systemu Windows XP i Windows 7. Zobacz [te informacje](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Przyczyny i zalecenia

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a>Urządzenie zdalne jest niedoścignialne

Jeśli nie można połączyć się przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP. Można użyć `ipconfig` w wierszu polecenia na komputerze zdalnym, aby uzyskać adres IPv4. Jeśli używasz pliku HOSTS, sprawdź, czy jest on poprawnie skonfigurowany.

Jeśli to się nie powiedzie, sprawdź, czy komputer zdalny jest dostępny w sieci[(ping komputera](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) zdalnego). Zdalne debugowanie przez Internet nie jest obsługiwane, z wyjątkiem niektórych scenariuszy platformy Microsoft Azure.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>Nazwa serwera jest nieprawidłowa lub oprogramowanie innych firm zakłóca działanie zdalnego debugera

W programie Visual Studio przyjrzyj się właściwościom projektu i upewnij się, że nazwa serwera jest poprawna. Zobacz tematy dotyczące [języka C# i Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) oraz [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). W przypadku ASP.NET otwórz w **zależności** od typu projektu, otwórz w zależności od typu **projektu, otwórz**

> [!NOTE]
> Jeśli do procesu są dołączane, ustawienia zdalne we właściwościach projektu nie są używane.

Jeśli nazwa serwera jest poprawna, oprogramowanie antywirusowe lub zapora innej firmy mogą blokować debuger zdalny. Podczas debugowania lokalnie może się to zdarzyć, ponieważ visual studio jest aplikacją 32-bitową, więc używa 64-bitowej wersji zdalnego debugera do debugowania aplikacji 64-bitowych. Procesy 32-bitowe i 64-bitowe komunikują się za pomocą sieci lokalnej na komputerze lokalnym. Żaden ruch sieciowy nie opuszcza komputera, ale możliwe jest, że oprogramowanie zabezpieczające innych firm może zablokować komunikację.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>Debuger zdalny działa na innym koncie użytkownika

Debuger zdalny domyślnie będzie akceptował tylko połączenia od użytkownika, który uruchomił debuger zdalny i członków grupy Administratorzy. Dodatkowi użytkownicy muszą mieć jawnie przyznane uprawnienia.

Można rozwiązać ten problem w jeden z następujących sposobów:

- Dodaj użytkownika programu Visual Studio do uprawnień debugera zdalnego (w oknie zdalnego debugera wybierz pozycję **Narzędzia > uprawnienia**).

- Na komputerze zdalnym uruchom ponownie debuger zdalny przy użyciu tego samego konta użytkownika i hasła, którego używasz na komputerze programu Visual Studio.

    > [!NOTE]
    > Jeśli debuger zdalny jest uruchamiany na serwerze zdalnym, kliknij prawym przyciskiem myszy aplikację Zdalny debuger i wybierz polecenie **Uruchom jako administrator** (Lub możesz uruchomić debuger zdalny jako usługę). Jeśli nie korzystasz z niego na serwerze zdalnym, po prostu uruchom go normalnie.

- Debuger zdalny można uruchomić z wiersza polecenia z parametrem `msvsmon /allow <username@computer>` **/allow \<>użytkownika:** .

- Alternatywnie można zezwolić każdemu użytkownikowi na zdalne debugowanie. W oknie zdalnego debugera przejdź do okna dialogowego **Narzędzia > Opcje.** Po wybraniu opcji **Brak uwierzytelniania**można następnie **zaznaczyć opcję Zezwalaj każdemu użytkownikowi na debugowanie**. Należy jednak wypróbować tę opcję tylko wtedy, gdy inne opcje nie powiodą się lub jeśli korzystasz z sieci prywatnej.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>Zapora na komputerze zdalnym nie zezwala na połączenia przychodzące z debugerem zdalnym
 Zapora na komputerze programu Visual Studio i zapora na komputerze zdalnym muszą być skonfigurowane tak, aby umożliwić komunikację między programem Visual Studio a debugerem zdalnym. Aby uzyskać informacje o portach używanych przez debuger [zdalny, zobacz Przydziały portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje dotyczące konfigurowania Zapory systemu Windows, zobacz [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie jest zgodna z wersją programu Visual Studio
 Wersja programu Visual Studio, która jest uruchomiona lokalnie, musi być zgodna z wersją monitora zdalnego debugowania uruchomionego na komputerze zdalnym. Aby rozwiązać ten problem, pobierz i zainstaluj pasującą wersję monitora zdalnego debugowania. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [Debugowanie zdalne](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Komputery lokalne i zdalne mają różne tryby uwierzytelniania
 Komputery lokalne i zdalne muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że oba komputery używają tego samego trybu uwierzytelniania. Można zmienić tryb uwierzytelniania. W oknie zdalnego debugera przejdź do okna dialogowego **Narzędzia > Opcje.**

 Aby uzyskać więcej informacji na temat trybów uwierzytelniania, zobacz [Omówienie uwierzytelniania systemu Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia
 Oprogramowanie antywirusowe systemu Windows umożliwia zdalne debuger połączenia, ale niektóre programy antywirusowe innych firm mogą je blokować. Zapoznaj się z dokumentacją oprogramowania antywirusowego, aby dowiedzieć się, jak zezwolić na te połączenia.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokują komunikację między komputerem zdalnym a programem Visual Studio
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci systemu Windows, zobacz [Ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęta, aby obsługiwać zdalne debugowanie
 Może być konieczne zdalne debugowanie w innym czasie lub ponowne zaplanowanie pracy w sieci na inny czas.

## <a name="more-help"></a>Więcej pomocy
 Aby uzyskać więcej pomocy debugera zdalnego, otwórz stronę Pomocy debugera zdalnego (**Pomoc > Użycie** w debugerze zdalnym).

## <a name="see-also"></a>Zobacz też
- [Zdalne debugowanie](../debugger/remote-debugging.md)
