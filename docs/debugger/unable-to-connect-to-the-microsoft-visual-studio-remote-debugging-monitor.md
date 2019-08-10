---
title: Nie można nawiązać połączenia z Monitor zdalnego debugowania Microsoft Visual Studio | Microsoft Docs
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
ms.openlocfilehash: c42cdfc5c3f3c0267fdcbdfca8ddc4bb30663384
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924525"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
Ten komunikat może wystąpić, ponieważ Monitor zdalnego debugowania nie jest prawidłowo skonfigurowany na maszynie zdalnej lub maszyna zdalna jest niedostępna z powodu problemów z siecią lub obecności zapory.

> [!IMPORTANT]
> Jeśli uważasz, że ta wiadomość została odebrana z powodu błędu produktu, [Zgłoś ten problem](../ide/how-to-report-a-problem-with-visual-studio.md) w programie Visual Studio. Jeśli potrzebujesz więcej pomocy, zobacz [Porozmawiaj z nami](../ide/talk-to-us.md) sposobów na kontakt z firmą Microsoft.

## <a name="specificerrors"></a>Co to jest szczegółowy komunikat o błędzie?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Komunikat jest ogólny. Zwykle w ciągu błędu jest zawarty bardziej szczegółowy komunikat, który może pomóc w zidentyfikowaniu przyczyny problemu lub wyszukaniu bardziej dokładnej poprawki. Poniżej przedstawiono kilka typowych komunikatów o błędach, które są dołączane do głównego komunikatu o błędzie:

- [Debuger nie może nawiązać połączenia z komputerem zdalnym. Debuger nie mógł rozpoznać określonej nazwy komputera](#cannot_connect)
- [Żądanie połączenia zostało odrzucone przez zdalny debuger](#rejected)
- [Nieprawidłowy dostęp do lokalizacji pamięci](#invalid_access)
- [Nie ma serwera o określonej nazwie uruchomionego na komputerze zdalnym](#no_server)
- [Żądana nazwa jest prawidłowa, ale nie znaleziono danych żądanego typu](#valid_name)
- [zdalny debuger programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](#cant_connect_back)
- [Odmowa dostępu](#access_denied)
- [Wystąpił błąd specyficzny dla pakietu zabezpieczeń](#security_package)

## <a name="cannot_connect"></a>Debuger nie może nawiązać połączenia z komputerem zdalnym. Debuger nie mógł rozpoznać określonej nazwy komputera

Spróbuj wykonać następujące czynności:

1. Upewnij się, że wprowadzono prawidłową nazwę komputera i numer portu w oknie dialogowym **Dołącz do procesu** lub we właściwościach projektu (aby ustawić właściwości, zobacz [te kroki](#server_incorrect)). Nazwa komputera musi mieć następujący format:

    `computername:port`

    > [!NOTE]
    > Numer portu musi być zgodny z [numerem portu zdalnego debugera](../debugger/remote-debugger-port-assignments.md), który *musi być uruchomiony* na maszynie docelowej.

2. Jeśli nazwa komputera nie działa, wypróbuj zamiast niego adres IP i numer portu.

3. Upewnij się, że wersja zdalnego debugera uruchomionego na maszynie docelowej jest zgodna z wersją programu Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

    > [!TIP]
    > Jeśli dołączysz do procesu i nawiążesz połączenie, ale nie widzisz żądanego procesu, zaznacz **pole wyboru Pokaż procesy dla wszystkich użytkowników**. Spowoduje to wyświetlenie procesów, jeśli masz połączenie przy użyciu innego konta użytkownika.

4. Jeśli te kroki nie rozwiązują tego błędu, zobacz, [że maszyna zdalna jest](#dns)nieosiągalna.

## <a name="rejected"></a>Żądanie połączenia zostało odrzucone przez zdalny debuger

W oknie dialogowym **Dołącz do procesu** lub we właściwościach projektu upewnij się, że nazwa komputera zdalnego i numer portu są zgodne z nazwą i numerem portu pokazanym w oknie debugera zdalnego. Jeśli jest nieprawidłowa, napraw i spróbuj ponownie.

Jeśli te wartości są poprawne, a komunikat wymienia tryb **uwierzytelniania systemu Windows** , sprawdź, czy zdalny debuger znajduje się w poprawnym trybie uwierzytelniania (**Narzędzia > Opcje**).

## <a name="invalid_access"></a>Nieprawidłowy dostęp do lokalizacji pamięci

Wystąpił błąd wewnętrzny. Uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="no_server"></a>Nie ma serwera o określonej nazwie uruchomionego na komputerze zdalnym

Program Visual Studio nie może nawiązać połączenia ze zdalnym debugerem. Ten komunikat może wystąpić z kilku powodów:

- Zdalny debuger może być uruchomiony przy użyciu innego konta użytkownika. Zobacz [te kroki](#user_accounts)

- Port jest zablokowany przez zaporę. Upewnij się, że Zapora [nie blokuje żądania](#firewall), zwłaszcza jeśli używasz zapory innej firmy.

- Wersja debugera zdalnego nie jest zgodna z Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="valid_name"></a>Żądana nazwa jest prawidłowa, ale nie znaleziono danych żądanego typu

Komputer zdalny istnieje, ale program Visual Studio nie może nawiązać połączenia ze zdalnym debugerem. Ten komunikat może wystąpić z kilku powodów:

- Problem z usługą DNS uniemożliwia połączenie. Zobacz [te kroki](#dns).

- Zdalny debuger może być uruchomiony przy użyciu innego konta użytkownika. Wykonaj [te kroki](#user_accounts).

- Port jest zablokowany przez zaporę. Upewnij się, że Zapora [nie blokuje żądania](#firewall), zwłaszcza jeśli używasz zapory innej firmy.

- Wersja debugera zdalnego nie jest zgodna z Visual Studio. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a>zdalny debuger programu Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem

Zdalny debuger może być uruchomiony przy użyciu innego konta użytkownika. W debugerze zdalnym otwórz pozycję **narzędzia > uprawnienia** , aby dodać użytkownika do uprawnień zdalnego debugera. Aby uzyskać więcej informacji, zobacz [zdalny debuger jest uruchomiony przy użyciu innego konta użytkownika](#user_accounts).

Jeśli komunikat o błędzie zawiera również zaporę, Zapora na komputerze lokalnym może uniemożliwiać komunikację z komputerem zdalnym z powrotem do programu Visual Studio. Zobacz [te kroki](#firewall).

## <a name="access_denied"></a>Odmowa dostępu

Ten błąd może pojawić się w przypadku próby debugowania na 64-bitowym komputerze zdalnym z komputera 32-bitowego (nieobsługiwane).

## <a name="security_package"></a>Wystąpił błąd specyficzny dla pakietu zabezpieczeń

Może to być starszy problem dotyczący systemów Windows XP i Windows 7. Zobacz te [informacje](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Przyczyny i zalecenia

### <a name="dns"></a>Maszyna zdalna jest nieosiągalna

Jeśli nie można nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP. Aby uzyskać adres `ipconfig` IPv4, można użyć w wierszu polecenia na komputerze zdalnym. Jeśli używasz pliku HOSTs, sprawdź, czy jest prawidłowo skonfigurowany.

Jeśli to się nie powiedzie, sprawdź, czy komputer zdalny jest dostępny w sieci ([Wyślij polecenie ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) do maszyny zdalnej). Debugowanie zdalne przez Internet nie jest obsługiwane, z wyjątkiem niektórych Microsoft Azure scenariuszy.

### <a name="server_incorrect"></a>Nazwa serwera jest niepoprawna lub oprogramowanie innych firm zakłóca zdalny debuger

W programie Visual Studio Sprawdź właściwości projektu i upewnij się, że nazwa serwera jest poprawna. Zobacz tematy dotyczące [ C# i Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) i [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). W przypadku ASP.NET Otwórz **właściwości/sieci Web/serwery** lub **Właściwości/Debuguj** w zależności od typu projektu.

> [!NOTE]
> W przypadku dołączania do procesu Ustawienia zdalne we właściwościach projektu nie są używane.

Jeśli nazwa serwera jest poprawna, oprogramowanie antywirusowe lub zapora innej firmy może blokować zdalny debuger. W przypadku debugowania lokalnego może to być spowodowane tym, że program Visual Studio jest aplikacją 32-bitową, więc używa wersji 64-bitowej zdalnego debugera do debugowania aplikacji 64-bitowych. Procesy 32-bitowe i 64-bitowe komunikują się przy użyciu sieci lokalnej na komputerze lokalnym. Żaden ruch sieciowy nie opuszcza komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innej firmy może blokować komunikację.

### <a name="user_accounts"></a>Zdalny debuger działa na innym koncie użytkownika

Zdalny debuger domyślnie akceptuje tylko połączenia od użytkownika, który uruchomił zdalny debuger i członków grupy Administratorzy. Dodatkowi użytkownicy muszą mieć jawnie przyznane uprawnienia.

Problem można rozwiązać w jednym z następujących sposobów:

- Dodaj użytkownika programu Visual Studio do uprawnień zdalnego debugera (w oknie Debuger zdalny wybierz pozycję **narzędzia > uprawnienia**).

- Na komputerze zdalnym ponownie uruchom zdalny debuger w ramach tego samego konta użytkownika i hasła, które są używane na komputerze programu Visual Studio.

    > [!NOTE]
    > Jeśli używasz zdalnego debugera na serwerze zdalnym, kliknij prawym przyciskiem myszy aplikację Remote Debugger i wybierz polecenie **Uruchom jako administrator** (lub, aby uruchomić zdalny debuger jako usługę). Jeśli nie jest uruchomiony na serwerze zdalnym, wystarczy uruchomić go normalnie.

- Zdalny debuger można uruchomić z wiersza polecenia z parametrem  **\</Allow username >** :. `msvsmon /allow <username@computer>`

- Alternatywnie można zezwolić każdemu użytkownikowi na zdalne debugowanie. W oknie zdalnego debugera, przejdź do **Narzędzia > Opcje** okna dialogowego. Po wybraniu **bez uwierzytelniania**, można sprawdzić **Zezwalaj dowolnemu użytkownikowi na debugowanie**. Należy jednak spróbować wykonać tę opcję tylko wtedy, gdy inne opcje zakończą się niepowodzeniem lub jeśli jesteś w sieci prywatnej.

### <a name="firewall"></a>Zapora na maszynie zdalnej nie zezwala na połączenia przychodzące ze zdalnym debugerem
 Zapora na komputerze programu Visual Studio, a zapora na zdalnym komputerze musi być skonfigurowany do zezwalania na komunikację między Visual Studio i zdalnym debugerem. Aby uzyskać informacji o portach używa zdalnego debugera, zobacz [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory Windows, zobacz [skonfigurować zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie pasuje do wersji programu Visual Studio
 Wersję programu Visual Studio, które działają lokalnie musi być zgodna z wersją monitor debugera zdalnego działa na komputerze zdalnym. Aby rozwiązać ten problem, należy pobrać i zainstalować zgodną wersję monitor debugera zdalnego. Aby uzyskać poprawną wersję zdalnego debugera, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Maszyny lokalne i zdalne mają tryby uwierzytelniania innego
 Maszyn lokalnych i zdalnych muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny będą używać trybu uwierzytelniania. Można zmienić tryb uwierzytelniania. W oknie zdalny debuger przejdź do okna dialogowego **narzędzia > opcje** .

 Aby uzyskać więcej informacji na temat trybów uwierzytelniana, zobacz [omówienie uwierzytelniania Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia
 Program antywirusowy Windows zezwala na połączenia zdalnego debugera, ale niektóre programy antywirusowe innej firmy mogą je zablokować. Sprawdź w dokumentacji oprogramowanie antywirusowe dowiedzieć się, jak umożliwić tych połączeń.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokuje komunikację między komputerem zdalnym i programu Visual Studio
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci Windows zobacz [ustawienia zasad zabezpieczeń](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęty, aby zapewnić obsługę zdalnego debugowania
 Może być konieczne przeprowadzać debugowanie zdalne w innym czasie lub Zmień harmonogram pracy w sieci inny czas.

## <a name="more-help"></a>Więcej pomocy
 Aby uzyskać więcej pomocy dotyczącej zdalnego debugera, Otwórz stronę pomocy zdalnego debugera (**pomoc > użyciu** w debugerze zdalnym).

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)
