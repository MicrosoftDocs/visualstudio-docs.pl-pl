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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477065"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nie można połączyć się z Monitorem debugera zdalnego programu Microsoft Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten komunikat o błędzie pojawia się po wprowadzeniu nieprawidłowej nazwy programu Visual Studio Monitor zdalnego debugowania w oknie dialogowym **Dołącz do procesu** . Nazwa Monitor zdalnego debugowania jest zwykle taka sama jak maszyna, z którą próbujesz nawiązać połączenie w celu debugowania zdalnego. Ten komunikat może wystąpić, ponieważ maszyna zdalna nie istnieje w sieci, Monitor zdalnego debugowania nie jest prawidłowo skonfigurowany na komputerze zdalnym lub maszyna zdalna jest niedostępna z powodu problemów z siecią lub obecności zapory.  
  
> [!IMPORTANT]
> Jeśli potrzebujesz więcej pomocy, skontaktuj się [z nami](../ide/talk-to-us.md) , aby dowiedzieć się, jak skontaktować się z firmą Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Mam ten komunikat podczas debugowania lokalnego  
 Jeśli ten komunikat jest wyświetlany podczas debugowania lokalnego, oprogramowanie antywirusowe lub zapora innej firmy może być polecenia Blame. Program Visual Studio jest aplikacją 32-bitową, więc używa wersji 64-bitowej zdalnego debugera do debugowania aplikacji 64-bitowych. Dwa procesy komunikują się przy użyciu sieci lokalnej na komputerze lokalnym. Żaden ruch sieciowy nie opuszcza komputera, ale istnieje możliwość, że oprogramowanie zabezpieczeń innej firmy może blokować komunikację.  
  
 W poniższych sekcjach wymieniono niektóre z tych powodów, dla których może zostać wyświetlony ten komunikat i co można zrobić, aby rozwiązać ten problem.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że Monitor zdalnego debugowania programu Visual Studio jest zainstalowana i uruchomiona na komputerze zdalnym. Aby uzyskać informacje o zdalnym debugerze i sposobie jego instalacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
- W programie Visual Studio zapoznaj się z właściwościami projektu (**Project/Properties/Debug**). Upewnij się, że **Nazwa serwera zdalnego** jest poprawna.  
  
- Sprawdź, czy maszyna zdalna jest dostępna w sieci.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Maszyna zdalna jest nieosiągalna  
 Spróbuj [wysłać polecenie ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) do komputera zdalnego. Jeśli nie odpowiada na polecenie ping, narzędzia zdalne nie będą mogły nawiązywać połączenia. Spróbuj ponownie uruchomić maszynę zdalną i w inny sposób upewnij się, że jest prawidłowo skonfigurowana w sieci.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Wersja zdalnego debugera nie jest zgodna z wersją programu Visual Studio  
 Wersja programu Visual Studio, która jest uruchamiana lokalnie, musi być zgodna z wersją monitora debugowania zdalnego, który jest uruchomiony na komputerze zdalnym. Aby rozwiązać ten problem, Pobierz i zainstaluj zgodną wersję monitora zdalnego debugowania. Przejdź do [subskrypcji programu Visual Studio](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) , aby znaleźć odpowiednią wersję zdalnego debugera dla używanej wersji programu Visual Studio.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Komputery lokalne i zdalne mają różne tryby uwierzytelniania  

 Maszyny lokalne i zdalne muszą korzystać z tego samego trybu uwierzytelniania. Aby rozwiązać ten problem, upewnij się, że obie maszyny używają tego samego trybu uwierzytelniania. Tryb uwierzytelniania można zmienić na zdalnym debugerze w oknie dialogowym **Narzędzia/Opcje** .  
  
 Aby uzyskać więcej informacji na temat trybów uwierzytelniania, zobacz [Omówienie uwierzytelniania systemu Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Zdalny debuger działa na innym koncie użytkownika  
 Można to rozwiązać w jeden z następujących sposobów:  
  
- Można zatrzymać zdalny debuger i uruchomić go ponownie przy użyciu konta używanego na komputerze lokalnym.  
  
- Zdalny debuger można uruchomić z wiersza polecenia z parametrem **/Allow \<username> ** :`msvsmon /allow <username@computer>`  
  
- Możesz dodać użytkownika do uprawnień zdalnego debugera (w oknie zdalny debuger, **Narzędzia/uprawnienia**).  
  
- Jeśli nie można użyć metod w powyższych krokach, można zezwolić każdemu użytkownikowi na zdalne debugowanie. W oknie Debuger zdalny przejdź do okna dialogowego **Narzędzia/Options** . W przypadku wybrania opcji   **Brak uwierzytelniania**można zaznaczyć pole wyboru **Zezwalaj każdemu użytkownikowi na Debugowanie**. Należy jednak użyć tej opcji tylko wtedy, gdy nie masz wyboru lub jeśli jesteś w sieci prywatnej.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Zapora na maszynie zdalnej nie zezwala na połączenia przychodzące ze zdalnym debugerem  
 Zapora na komputerze z programem Visual Studio i Zapora na maszynie zdalnej musi być skonfigurowana w taki sposób, aby zezwalała na komunikację między programem Visual Studio i zdalnym debugerem. Informacje o portach, które są używane przez zdalny debuger, można znaleźć w temacie [przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Aby uzyskać informacje o konfigurowaniu zapory systemu Windows, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Oprogramowanie antywirusowe blokuje połączenia  
 Oprogramowanie antywirusowe systemu Windows umożliwia połączenia zdalnego debugera, ale niektóre oprogramowanie antywirusowe innej firmy może je zablokować. Zapoznaj się z dokumentacją oprogramowania antywirusowego, aby dowiedzieć się, jak zezwolić na te połączenia.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zasady zabezpieczeń sieci blokują komunikację między maszyną zdalną a programem Visual Studio  
 Sprawdź zabezpieczenia sieci, aby upewnić się, że nie blokuje ona komunikacji. Aby uzyskać więcej informacji na temat zasad zabezpieczeń sieci systemu Windows, zobacz [Zarządzanie zabezpieczeniami](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Sieć jest zbyt zajęta, aby obsługiwać debugowanie zdalne  
 Może być konieczne przeprowadzenie debugowania zdalnego w innym czasie lub ponowne zaplanowanie pracy w sieci przez inny czas.  
  
## <a name="more-help"></a>Więcej pomocy  
 Aby uzyskać więcej pomocy dotyczącej zdalnego debugera, w tym przełączników wiersza polecenia, Otwórz następujące polecenie w przeglądarce:  
  
 **res://C: \Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote% 20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
