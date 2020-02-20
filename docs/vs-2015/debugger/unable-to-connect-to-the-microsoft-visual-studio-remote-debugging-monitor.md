---
title: Nie można nawiązać połączenia z Monitor zdalnego debugowania Microsoft Visual Studio | Microsoft Docs
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
ms.openlocfilehash: d62e7ce1c419a9c53e40e1ecf2f71497d60d7a23
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477065"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten komunikat o błędzie pojawia się po wprowadzeniu nieprawidłowej nazwy programu Visual Studio Monitor zdalnego debugowania w oknie dialogowym **Dołącz do procesu** . Nazwa Monitor zdalnego debugowania jest zwykle taka sama jak maszyna, z którą próbujesz nawiązać połączenie w celu debugowania zdalnego. Ten komunikat może wystąpić, ponieważ maszyna zdalna nie istnieje w sieci, Monitor zdalnego debugowania nie jest prawidłowo skonfigurowany na komputerze zdalnym lub maszyna zdalna jest niedostępna z powodu problemów z siecią lub obecności zapory.  
  
> [!IMPORTANT]
> Jeśli potrzebujesz więcej pomocy, skontaktuj się [z nami](../ide/talk-to-us.md) , aby dowiedzieć się, jak skontaktować się z firmą Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Został wyświetlony komunikat, gdy został I debugowanie lokalnie  
 Jeśli otrzymujesz ten komunikat, gdy debugujesz lokalnie, oprogramowanie antywirusowe lub zapory innych firm może być stronę. Visual Studio to 32-bitowej aplikacji, więc używa 64-bitowej wersji zdalnego debugera do debugowania 64-bitowych aplikacji. Dwa procesy komunikacji za pośrednictwem sieci lokalnej na komputerze lokalnym. Żaden ruch sieciowy nie opuszcza komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innej firmy może blokować komunikację.  
  
 W poniższych sekcjach wymieniono niektóre inne przyczyny, dlaczego użytkownik może stają się coraz ten komunikat i co można zrobić, aby rozwiązać ten problem.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że Monitor zdalnego debugowania programu Visual Studio jest zainstalowana i uruchomiona na komputerze zdalnym. Aby uzyskać informacje o zdalnym debugerze i sposobie jego instalacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
- W programie Visual Studio zapoznaj się z właściwościami projektu (**Project/Properties/Debug**). Upewnij się, że **Nazwa serwera zdalnego** jest poprawna.  
  
- Sprawdź, czy maszyna zdalna jest dostępna w sieci.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Maszyna zdalna nie jest dostępny  
 Spróbuj [wysłać polecenie ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) do komputera zdalnego. Jeśli nie odpowiada na polecenie ping, narzędzia zdalne nie będą mogły nawiązywać połączenia. Spróbuj ponownie uruchamiając komputer zdalny, a w przeciwnym razie upewniając się, że została poprawnie skonfigurowana w sieci.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie jest zgodna z wersją programu Visual Studio  
 Wersję programu Visual Studio, które działają lokalnie musi być zgodna z wersją monitor debugera zdalnego działa na komputerze zdalnym. Aby rozwiązać ten problem, należy pobrać i zainstalować zgodną wersję monitor debugera zdalnego. Przejdź do [subskrypcji programu Visual Studio](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) , aby znaleźć odpowiednią wersję zdalnego debugera dla używanej wersji programu Visual Studio.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Maszyny lokalne i zdalne mają tryby uwierzytelniania innego  

 Maszyn lokalnych i zdalnych muszą używać tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny będą używać trybu uwierzytelniania. Tryb uwierzytelniania można zmienić na zdalnym debugerze w oknie dialogowym **Narzędzia/Opcje** .  
  
 Aby uzyskać więcej informacji na temat trybów uwierzytelniania, zobacz [Omówienie uwierzytelniania systemu Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Debuger zdalny jest uruchomiony w ramach konta innego użytkownika  
 Problem można rozwiązać w jednym z następujących sposobów:  
  
- Można zatrzymać debuger zdalny i uruchom go ponownie przy użyciu konta, którego używasz na komputerze lokalnym.  
  
- Zdalny debuger można uruchomić z wiersza polecenia z parametrem **/allow \<username >** : `msvsmon /allow <username@computer>`  
  
- Możesz dodać użytkownika do uprawnień zdalnego debugera (w oknie zdalny debuger, **Narzędzia/uprawnienia**).  
  
- Jeśli nie możesz użyć metody w poprzednich krokach, możesz zezwolić użytkownikowi przeprowadzać debugowanie zdalne. W oknie Debuger zdalny przejdź do okna dialogowego **Narzędzia/Options** . W przypadku wybrania opcji **Brak uwierzytelniania**można zaznaczyć pole wyboru **Zezwalaj każdemu użytkownikowi na Debugowanie**. Jednak należy używać tej opcji tylko wtedy, gdy możesz nie mieć wyboru, czy znajdują się w sieci prywatnej.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Zapora na maszynie zdalnej nie zezwala na połączenia przychodzące ze zdalnym debugerem  
 Zapora na komputerze programu Visual Studio, a zapora na zdalnym komputerze musi być skonfigurowany do zezwalania na komunikację między Visual Studio i zdalnym debugerem. Informacje o portach, które są używane przez zdalny debuger, można znaleźć w temacie [przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory systemu Windows, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia  
 Program antywirusowy Windows zezwala na połączenia zdalnego debugera, ale niektóre programy antywirusowe innej firmy mogą je zablokować. Sprawdź w dokumentacji oprogramowanie antywirusowe dowiedzieć się, jak umożliwić tych połączeń.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokuje komunikację między komputerem zdalnym i programu Visual Studio  
 Przejrzyj zabezpieczenia sieci, aby upewnić się, że nie blokuje komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci systemu Windows, zobacz [Zarządzanie zabezpieczeniami](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęty, aby zapewnić obsługę zdalnego debugowania  
 Może być konieczne przeprowadzać debugowanie zdalne w innym czasie lub Zmień harmonogram pracy w sieci inny czas.  
  
## <a name="more-help"></a>Więcej pomocy  
 Aby uzyskać więcej pomocy dotyczącej zdalnego debugera, w tym przełączników wiersza polecenia, Otwórz następujące polecenie w przeglądarce:  
  
 **res://C: \ Program %2 0 pliki \ Microsoft %2 0 Visual %2 0 Studio% 2014.0 \ Common7 \ IDE \ Remote %2 0 Debugger \ x64 \ msvsmon. exe/help. htm**  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
