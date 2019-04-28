---
title: Nie można nawiązać połączenia z programem Microsoft Visual Studio Monitor debugera zdalnego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db946e2dfac035a8e0ddb5581c37e36b0406fb24
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437780"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten komunikat o błędzie jest wyświetlany, gdy wprowadzasz Nieprawidłowa nazwa programu Visual Studio Monitor zdalnego debugowania w **dołączyć do procesu** okno dialogowe. Nazwa monitora debugera zdalnego jest zwykle taka sama jak komputer, do którego próbujesz nawiązać połączenie zdalne debugowanie. Ten komunikat może wystąpić, ponieważ Maszyna zdalna nie istnieje w sieci, monitor debugera zdalnego jest nie prawidłowo skonfigurowane na komputerze zdalnym lub maszynie zdalnej jest niedostępny z powodu problemów z siecią lub obecności zapory.  
  
> [!IMPORTANT]
> Jeśli uważasz, że ten komunikat został przesłany z powodu błędu w produkcie, zgłoś ten problem w programie Visual Studio [Wyślij uśmiech](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b). Jeśli potrzebujesz więcej pomocy, zobacz [Porozmawiaj z nami](../ide/talk-to-us.md) sposobów na kontakt z firmą Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Został wyświetlony komunikat, gdy został I debugowanie lokalnie  
 Jeśli otrzymujesz ten komunikat, gdy debugujesz lokalnie, oprogramowanie antywirusowe lub zapory innych firm może być stronę. Visual Studio to 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania 64-bitowych aplikacji. Dwa procesy komunikacji za pośrednictwem sieci lokalnej na komputerze lokalnym. Żaden ruch sieciowy pozostawia komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innych firm mogą blokować komunikacji.  
  
 W poniższych sekcjach wymieniono niektóre inne przyczyny, dlaczego użytkownik może stają się coraz ten komunikat i co można zrobić, aby rozwiązać ten problem.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że Monitor programu Visual Studio zdalne debugowanie jest zainstalowana i uruchomiona na komputerze zdalnym. Aby uzyskać informacje o zdalnym debugerem i sposobach jego instalacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
- W programie Visual Studio, Przyjrzyj się właściwości projektu (**projekt / właściwości / debugowania**). Upewnij się, że **nazwa serwera zdalnego** jest poprawna.  
  
- Sprawdź, czy komputer zdalny jest dostępny w sieci.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Maszyna zdalna nie jest dostępny  
 Spróbuj [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) maszyny zdalnej. Jeśli go nie odpowiada na polecenie ping, narzędzi zdalnych nie będzie można połączyć w jedną. Spróbuj ponownie uruchamiając komputer zdalny, a w przeciwnym razie upewniając się, że została poprawnie skonfigurowana w sieci.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie pasuje do wersji programu Visual Studio  
 Wersję programu Visual Studio, które działają lokalnie musi być zgodna z wersją monitor debugera zdalnego działa na komputerze zdalnym. Aby rozwiązać ten problem, należy pobrać i zainstalować zgodną wersję monitor debugera zdalnego. Przejdź do [Centrum pobierania](http://www.microsoft.com/download) można znaleźć właściwą wersję zdalnego debugera.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Maszyny lokalne i zdalne mają tryby uwierzytelniania innego  
 Maszyn lokalnych i zdalnych muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny będą używać trybu uwierzytelniania. Możesz zmienić tryb uwierzytelniania zdalnego debugera w **narzędzia / Opcje** okna dialogowego.  
  
 Aby uzyskać więcej informacji na temat trybów uwierzytelniana, zobacz [omówienie uwierzytelniania Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Debuger zdalny jest uruchomiony w ramach konta innego użytkownika  
 Problem można rozwiązać w jednym z następujących sposobów:  
  
- Można zatrzymać debuger zdalny i uruchom go ponownie przy użyciu konta, którego używasz na komputerze lokalnym.  
  
- Zdalny debuger można uruchomić z wiersza polecenia za pomocą **/ allow \<username >** parametru: `msvsmon /allow <username@computer>`  
  
- Można dodać użytkownika do zdalnego debugera uprawnień (w oknie debugera zdalnego **narzędzia / uprawnienia**).  
  
- Jeśli nie możesz użyć metody w poprzednich krokach, możesz zezwolić użytkownikowi przeprowadzać debugowanie zdalne. W oknie zdalnego debugera, przejdź do **/Options narzędzia** okna dialogowego. Po wybraniu **bez uwierzytelniania**, można sprawdzić **Zezwalaj dowolnemu użytkownikowi na debugowanie**. Jednak należy używać tej opcji tylko wtedy, gdy możesz nie mieć wyboru, czy znajdują się w sieci prywatnej.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Zapora na zdalnym komputerze nie zezwala na połączenia przychodzące do zdalnego debugera  
 Zapora na komputerze programu Visual Studio, a zapora na zdalnym komputerze musi być skonfigurowany do zezwalania na komunikację między Visual Studio i zdalnym debugerem. Aby uzyskać informacji o portach używa zdalnego debugera, zobacz [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory Windows, zobacz [skonfigurować zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia  
 Program antywirusowy Windows zezwala na połączenia zdalnego debugera, ale niektóre programy antywirusowe innej firmy mogą je zablokować. Sprawdź w dokumentacji oprogramowanie antywirusowe dowiedzieć się, jak umożliwić tych połączeń.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokuje komunikację między komputerem zdalnym i programu Visual Studio  
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci Windows zobacz [Zarządzanie zabezpieczeniami](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęty, aby zapewnić obsługę zdalnego debugowania  
 Może być konieczne przeprowadzać debugowanie zdalne w innym czasie lub Zmień harmonogram pracy w sieci inny czas.  
  
## <a name="more-help"></a>Więcej pomocy  
 Aby uzyskać więcej pomocy debugera, takich jak przełączniki wiersza polecenia, należy otworzyć następujące w przeglądarce:  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
