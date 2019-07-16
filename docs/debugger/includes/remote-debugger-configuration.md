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
1. Na komputerze zdalnym, należy znaleźć i uruchomić **zdalny debuger** z **Start** menu. 
   
   Jeśli nie masz uprawnienia administracyjne na komputerze zdalnym, kliknij prawym przyciskiem myszy **zdalny debuger** aplikacji i wybierz **Uruchom jako administrator**. W przeciwnym razie po prostu ją uruchomić normalnie.

   Jeśli planujesz dołączyć do procesu, który działa jako administrator, lub jest uruchomiona w ramach innego użytkownika konta (np. usługi IIS), kliknij prawym przyciskiem myszy **zdalny debuger** aplikacji i wybierz **Uruchom jako administrator**. Aby uzyskać więcej informacji, zobacz [uruchomić zdalny debuger jako administrator](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. Po raz pierwszy uruchomić zdalny debuger (lub został wcześniej skonfigurowany) **Konfiguracja zdalnego debugowania** pojawi się okno dialogowe.  
  
    ![Konfiguracji zdalnego debugera](../media/remotedebuggerconfwizardpage.png "konfiguracji zdalnego debugera")  
  
1. Jeśli API usług sieci Web Windows nie jest zainstalowany, które odbywa się tylko w systemie Windows Server 2008 R2, wybierz opcję **zainstalować** przycisku.  
  
1. Wybierz co najmniej jeden typ sieci chcesz używania narzędzi zdalnych na. Jeśli komputery są połączone za pośrednictwem domeny, należy wybrać pierwszy element. Komputery są połączone za pośrednictwem grupy roboczej lub grupa domowa, jeśli drugi lub trzeci element zgodnie z potrzebami.  
  
1. Wybierz **Konfiguruj zdalne debugowanie** Aby skonfigurować zaporę i uruchomić zdalny debuger.  
  
1. Po zakończeniu konfiguracji **zdalny debuger** zostanie wyświetlone okno.
  
    ![Okna debugera zdalnego](../media/remotedebuggerwindow.png "okna debugera zdalnego")
  
    Zdalny debuger jest teraz oczekiwania na połączenie. Użyj nazwy serwera i portu wynikową do ustawienia konfiguracji połączeń zdalnych w programie Visual Studio.  
  
Aby zatrzymać zdalnego debugera, wybierz **pliku** > **zakończenia**. Możesz ponownie uruchomić go z **Start** menu lub z wiersza polecenia:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
