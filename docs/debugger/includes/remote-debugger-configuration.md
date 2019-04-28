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
ms.openlocfilehash: d89dbc0b752c2b8c538ec53769c166b6edbd802f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902889"
---
1. Na komputerze zdalnym, należy znaleźć i uruchomić **zdalny debuger** z **Start** menu. 
   
   Jeśli nie masz uprawnienia administracyjne na komputerze zdalnym, kliknij prawym przyciskiem myszy **zdalny debuger** aplikacji i wybierz **Uruchom jako administrator**. W przeciwnym razie po prostu ją uruchomić normalnie.

   Może to być różne wersje *msvsmon.exe* w *x64*, *x32*, lub w innych folderach. Upewnij się, że jest uruchomiona wersja potrzebne do debugowania aplikacji. 
   
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
