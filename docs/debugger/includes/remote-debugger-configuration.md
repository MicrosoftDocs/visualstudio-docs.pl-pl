---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149172"
---
1. Na komputerze zdalnym Znajdź i uruchom **zdalny debuger** z menu **Start** . 
   
   Jeśli nie masz uprawnień administracyjnych na komputerze zdalnym, kliknij prawym przyciskiem myszy aplikację **Remote Debugger** i wybierz polecenie **Uruchom jako administrator**. W przeciwnym razie po prostu uruchom je normalnie.

   Jeśli planujesz dołączenie do procesu, który jest uruchomiony jako administrator lub działa na innym koncie użytkownika (na przykład IIS), kliknij prawym przyciskiem myszy aplikację **Remote Debugger** i wybierz polecenie **Uruchom jako administrator**. Aby uzyskać więcej informacji, zobacz [Uruchamianie debugera zdalnego jako administrator](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. Przy pierwszym uruchomieniu zdalnego debugera (lub przed jego skonfigurowaniem) zostanie wyświetlone okno dialogowe **Konfiguracja zdalnego debugowania** .  
  
    Konfiguracja(../media/remotedebuggerconfwizardpage.png "zdalnego debugera") ![konfiguracji debugera zdalnego]  
  
1. Jeśli nie zainstalowano interfejsu API usług sieci Web systemu Windows, który występuje tylko w systemie Windows Server 2008 R2, wybierz przycisk **Instaluj** .  
  
1. Wybierz co najmniej jeden typ sieci, na którym chcesz korzystać z narzędzi zdalnych. Jeśli komputery są połączone za pomocą domeny, należy wybrać pierwszy element. Jeśli komputery są połączone przez grupę roboczą lub grupę domową, wybierz drugi lub trzeci element stosownie do potrzeb.  
  
1. Wybierz pozycję **Konfiguruj zdalne debugowanie** , aby skonfigurować zaporę i uruchomić zdalny debuger.  
  
1. Po zakończeniu konfiguracji zostanie wyświetlone okno **zdalny debuger** .
  
    (../media/remotedebuggerwindow.png "Okno zdalnego debugera") ![okna debugera zdalnego]
  
    Zdalny debuger czeka teraz na połączenie. Użyj nazwy serwera i numeru portu podanego do ustawienia konfiguracji połączenia zdalnego w programie Visual Studio.  
  
Aby zatrzymać zdalny debuger **, wybierz pozycję**  >  **Zakończ**. Możesz uruchomić go ponownie z menu **Start** lub z wiersza polecenia:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
