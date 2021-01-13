---
title: Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
description: Poznaj znaczenie "nie można nawiązać połączenia z Microsoft Visual Studio Monitor zdalnego debugowania", możliwych przyczyn i rozwiązań.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: dc34a5f58f8bc3c47526cc8ba8516311e94f0631
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150837"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
Ten komunikat może wystąpić, ponieważ Monitor zdalnego debugowania nie jest prawidłowo skonfigurowany na maszynie zdalnej lub maszyna zdalna jest niedostępna z powodu problemów z siecią lub obecności zapory.

> [!IMPORTANT]
> Jeśli uważasz, że ta wiadomość została odebrana z powodu błędu produktu, [Zgłoś ten problem](../ide/how-to-report-a-problem-with-visual-studio.md) w programie Visual Studio. Jeśli potrzebujesz więcej pomocy, skontaktuj się [z nami](../ide/feedback-options.md) , aby dowiedzieć się, jak skontaktować się z firmą Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Co to jest szczegółowy komunikat o błędzie?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor`Komunikat jest ogólny. Zwykle w ciągu błędu jest zawarty bardziej szczegółowy komunikat, który może pomóc w zidentyfikowaniu przyczyny problemu lub wyszukaniu bardziej dokładnej poprawki. Poniżej przedstawiono kilka typowych komunikatów o błędach, które są dołączane do głównego komunikatu o błędzie:

- [Debuger nie może nawiązać połączenia z komputerem zdalnym. Debuger nie mógł rozpoznać określonej nazwy komputera](#cannot_connect)
- [Żądanie połączenia zostało odrzucone przez zdalny debuger](#rejected)
- [Połączenie ze zdalnym punktem końcowym zostało przerwane](#connection_terminated)
- [Nieprawidłowy dostęp do lokalizacji pamięci](#invalid_access)
- [Nie ma serwera o określonej nazwie uruchomionego na komputerze zdalnym](#no_server)
- [Żądana nazwa jest prawidłowa, ale nie znaleziono danych żądanego typu](#valid_name)
- [zdalny debuger programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](#cant_connect_back)
- [Odmowa dostępu](#access_denied)
- [Wystąpił błąd specyficzny dla pakietu zabezpieczeń](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a> Debuger nie może nawiązać połączenia z komputerem zdalnym. Debuger nie mógł rozpoznać określonej nazwy komputera

Wypróbuj następujące rozwiązania:

1. Upewnij się, że wprowadzono prawidłową nazwę komputera i numer portu w oknie dialogowym **Dołącz do procesu** lub we właściwościach projektu (aby ustawić właściwości, zobacz [te kroki](#server_incorrect)). Nazwa komputera musi mieć następujący format:

    `computername:port`

    > [!NOTE]
    > Numer portu musi być zgodny z [numerem portu zdalnego debugera](../debugger/remote-debugger-port-assignments.md), który *musi być uruchomiony* na maszynie docelowej.

2. Jeśli nazwa komputera nie działa, wypróbuj zamiast niego adres IP i numer portu.

3. Upewnij się, że wersja zdalnego debugera uruchomionego na maszynie docelowej jest zgodna z wersją programu Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

    > [!TIP]
    > Jeśli dołączysz do procesu i nawiążesz połączenie, ale nie widzisz żądanego procesu, zaznacz **pole wyboru Pokaż procesy dla wszystkich użytkowników**. Spowoduje to wyświetlenie procesów, jeśli masz połączenie przy użyciu innego konta użytkownika.

4. Jeśli te kroki nie rozwiązują tego błędu, zobacz, [że maszyna zdalna jest nieosiągalna](#dns).

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a> Żądanie połączenia zostało odrzucone przez zdalny debuger

W oknie dialogowym **Dołącz do procesu** lub we właściwościach projektu upewnij się, że nazwa komputera zdalnego i numer portu są zgodne z nazwą i numerem portu pokazanym w oknie debugera zdalnego. Jeśli jest nieprawidłowa, napraw i spróbuj ponownie.

Jeśli te wartości są poprawne, a komunikat wymienia tryb **uwierzytelniania systemu Windows** , sprawdź, czy zdalny debuger znajduje się w poprawnym trybie uwierzytelniania (**Narzędzia > opcje**).

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a> Połączenie ze zdalnym punktem końcowym zostało przerwane

Jeśli debugujesz aplikację Azure App Service, spróbuj użyć polecenia [Dołącz debuger](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) w Eksploratorze chmury lub Eksplorator serwera zamiast **dołączać do procesu**.

Jeśli używasz funkcji **Dołącz do procesu** do debugowania:

- W oknie dialogowym **Dołącz do procesu** lub we właściwościach projektu upewnij się, że nazwa komputera zdalnego i numer portu są zgodne z nazwą i numerem portu pokazanym w oknie debugera zdalnego. Jeśli jest nieprawidłowa, napraw i spróbuj ponownie.

- Jeśli próbujesz nawiązać połączenie przy użyciu nazwy hosta, zamiast tego spróbuj użyć adresu IP.

- Sprawdź dziennik aplikacji na serwerze (Podgląd zdarzeń w systemie Windows), aby uzyskać bardziej szczegółowe informacje pomocne w rozwiązaniu problemu.

- W przeciwnym razie spróbuj ponownie uruchomić program Visual Studio z uprawnieniami administratora, a następnie ponów próbę.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a> Nieprawidłowy dostęp do lokalizacji pamięci

Wystąpił błąd wewnętrzny. Uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a> Nie ma serwera o określonej nazwie uruchomionego na komputerze zdalnym

Program Visual Studio nie może nawiązać połączenia ze zdalnym debugerem. Ten komunikat może wystąpić z kilku powodów:

- Zdalny debuger może być uruchomiony przy użyciu innego konta użytkownika. Zobacz [te kroki](#user_accounts)

- Port jest zablokowany przez zaporę. Upewnij się, że Zapora [nie blokuje żądania](#firewall), zwłaszcza jeśli używasz zapory innej firmy.

- Wersja debugera zdalnego nie jest zgodna z Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a> Żądana nazwa jest prawidłowa, ale nie znaleziono danych żądanego typu

Komputer zdalny istnieje, ale program Visual Studio nie może nawiązać połączenia ze zdalnym debugerem. Ten komunikat może wystąpić z kilku powodów:

- Problem z usługą DNS uniemożliwia połączenie. Zobacz [te kroki](#dns).

- Zdalny debuger może być uruchomiony przy użyciu innego konta użytkownika. Wykonaj [te kroki](#user_accounts).

- Port jest zablokowany przez zaporę. Upewnij się, że Zapora [nie blokuje żądania](#firewall), zwłaszcza jeśli używasz zapory innej firmy.

- Wersja debugera zdalnego nie jest zgodna z Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a> zdalny debuger programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem

Zdalny debuger może być uruchomiony przy użyciu innego konta użytkownika. W debugerze zdalnym otwórz pozycję **narzędzia > uprawnienia** , aby dodać użytkownika do uprawnień zdalnego debugera. Aby uzyskać więcej informacji, zobacz [zdalny debuger jest uruchomiony przy użyciu innego konta użytkownika](#user_accounts).

Jeśli komunikat o błędzie zawiera również zaporę, Zapora na komputerze lokalnym może uniemożliwiać komunikację z komputerem zdalnym z powrotem do programu Visual Studio. Zobacz [te kroki](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a> Odmowa dostępu

Ten błąd może pojawić się w przypadku próby debugowania na 64-bitowym komputerze zdalnym z komputera 32-bitowego (nieobsługiwane).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a> Wystąpił błąd specyficzny dla pakietu zabezpieczeń

Może to być starszy problem dotyczący systemów Windows XP i Windows 7. Zobacz te [informacje](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Przyczyny i zalecenia

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> Maszyna zdalna jest nieosiągalna

Jeśli nie można nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP. `ipconfig`Aby uzyskać adres IPv4, można użyć w wierszu polecenia na komputerze zdalnym. Jeśli używasz pliku HOSTs, sprawdź, czy jest prawidłowo skonfigurowany.

Jeśli to się nie powiedzie, sprawdź, czy komputer zdalny jest dostępny w sieci ([Wyślij polecenie ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) do maszyny zdalnej). Debugowanie zdalne przez Internet nie jest obsługiwane, z wyjątkiem niektórych Microsoft Azure scenariuszy.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a> Nazwa serwera jest niepoprawna lub oprogramowanie innych firm zakłóca zdalny debuger

W programie Visual Studio Sprawdź właściwości projektu i upewnij się, że nazwa serwera jest poprawna. Zobacz tematy dla [języków C# i Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) i [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). W przypadku ASP.NET Otwórz **właściwości/sieci Web/serwery** lub **Właściwości/Debuguj** w zależności od typu projektu.

> [!NOTE]
> W przypadku dołączania do procesu Ustawienia zdalne we właściwościach projektu nie są używane.

Jeśli nazwa serwera jest poprawna, oprogramowanie antywirusowe lub zapora innej firmy może blokować zdalny debuger. W przypadku debugowania lokalnego może to być spowodowane tym, że program Visual Studio jest aplikacją 32-bitową, więc używa wersji 64-bitowej zdalnego debugera do debugowania aplikacji 64-bitowych. Procesy 32-bitowe i 64-bitowe komunikują się przy użyciu sieci lokalnej na komputerze lokalnym. Żaden ruch sieciowy nie opuszcza komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innej firmy może blokować komunikację.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a> Zdalny debuger działa na innym koncie użytkownika

Zdalny debuger domyślnie akceptuje tylko połączenia od użytkownika, który uruchomił zdalny debuger i członków grupy Administratorzy. Dodatkowi użytkownicy muszą mieć jawnie przyznane uprawnienia.

Można to rozwiązać w jeden z następujących sposobów:

- Dodaj użytkownika programu Visual Studio do uprawnień zdalnego debugera (w oknie Debuger zdalny wybierz pozycję **narzędzia > uprawnienia**).

- Na komputerze zdalnym ponownie uruchom zdalny debuger w ramach tego samego konta użytkownika i hasła, które są używane na komputerze programu Visual Studio.

    > [!NOTE]
    > Jeśli używasz zdalnego debugera na serwerze zdalnym, kliknij prawym przyciskiem myszy aplikację Remote Debugger i wybierz polecenie **Uruchom jako administrator** (lub, aby uruchomić zdalny debuger jako usługę). Jeśli nie jest uruchomiony na serwerze zdalnym, wystarczy uruchomić go normalnie.

- Zdalny debuger można uruchomić z wiersza polecenia z parametrem **/Allow \<username>** : `msvsmon /allow <username@computer>` .

- Alternatywnie można zezwolić każdemu użytkownikowi na zdalne debugowanie. W oknie Debuger zdalny przejdź do okna dialogowego **narzędzia > opcje** . W przypadku wybrania opcji   **Brak uwierzytelniania** można zaznaczyć pole wyboru **Zezwalaj każdemu użytkownikowi na Debugowanie**. Należy jednak spróbować wykonać tę opcję tylko wtedy, gdy inne opcje zakończą się niepowodzeniem lub jeśli jesteś w sieci prywatnej.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> Zapora na maszynie zdalnej nie zezwala na połączenia przychodzące ze zdalnym debugerem
 Zapora na komputerze z programem Visual Studio i Zapora na maszynie zdalnej musi być skonfigurowana w taki sposób, aby zezwalała na komunikację między programem Visual Studio i zdalnym debugerem. Informacje o portach, które są używane przez zdalny debuger, można znaleźć w temacie [przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory systemu Windows, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie jest zgodna z wersją programu Visual Studio
 Wersja programu Visual Studio, która jest uruchamiana lokalnie, musi być zgodna z wersją monitora debugowania zdalnego, który jest uruchomiony na komputerze zdalnym. Aby rozwiązać ten problem, Pobierz i zainstaluj zgodną wersję monitora zdalnego debugowania. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Komputery lokalne i zdalne mają różne tryby uwierzytelniania
 Maszyny lokalne i zdalne muszą korzystać z tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny używają tego samego trybu uwierzytelniania. Można zmienić tryb uwierzytelniania. W oknie zdalny debuger przejdź do okna dialogowego **narzędzia > opcje** .

 Aby uzyskać więcej informacji na temat trybów uwierzytelniania, zobacz [Omówienie uwierzytelniania systemu Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia
 Oprogramowanie antywirusowe systemu Windows umożliwia połączenia zdalnego debugera, ale niektóre oprogramowanie antywirusowe innej firmy może je zablokować. Zapoznaj się z dokumentacją oprogramowania antywirusowego, aby dowiedzieć się, jak zezwolić na te połączenia.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokują komunikację między maszyną zdalną a programem Visual Studio
 Sprawdź zabezpieczenia sieci, aby upewnić się, że nie blokuje ona komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci systemu Windows, zobacz [Ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęta, aby obsługiwać debugowanie zdalne
 Może być konieczne przeprowadzenie debugowania zdalnego w innym czasie lub ponowne zaplanowanie pracy w sieci przez inny czas.

## <a name="more-help"></a>Więcej pomocy
 Aby uzyskać więcej pomocy dotyczącej zdalnego debugera, Otwórz stronę pomocy zdalnego debugera (**pomoc > użyciu** w debugerze zdalnym).

## <a name="see-also"></a>Zobacz także
- [Debugowanie zdalne](../debugger/remote-debugging.md)
