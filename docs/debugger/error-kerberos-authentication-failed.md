---
title: 'Błąd: Uwierzytelnianie Kerberos nie powiodło się | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66e9ef1ee7ab969e8abb62e2e6886ee2e74c82f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854272"
---
# <a name="error-kerberos-authentication-failed"></a>Błąd: Uwierzytelnianie Kerberos nie powiodło się
Gdy użytkownik próbuje przeprowadzać debugowanie zdalne, może uzyskać następujący komunikat o błędzie:  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.  
```  
  
 Ten błąd występuje, gdy zdalny Monitor debugowania Visual Studio jest uruchomiony na koncie systemu lokalnego lub usługi sieciowej. W ramach jednego z tych kont debuger zdalny nawiązać połączenie uwierzytelniania Kerberos do komunikacji zwrotnej z komputera hosta debugera programu Visual Studio.  
  
 Uwierzytelnianie Kerberos nie jest dostępne w tych warunkach:  
  
- Na komputerze docelowym lub debugera komputer-host znajduje się w grupie roboczej, a nie do domeny  
  
   \- lub —  
  
- Protokołu Kerberos zostało wyłączone na kontrolerze domeny.  
  
  Jeśli uwierzytelnianie Kerberos nie jest dostępna, należy zmienić konto, które jest używane do uruchamiania programu Visual Studio Monitor zdalnego debugowania. Procedury można wyświetlić [błąd: Usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
  Jeśli oba komputery są połączone z tej samej domenie, a nadal otrzymujesz ten komunikat, sprawdź, czy DNS na komputerze docelowym jest poprawnie rozpoznawania nazwy komputera-hosta debugera. Zobacz poniższą procedurę.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Aby sprawdzić, czy DNS na komputerze docelowym poprawnie mapuje nazwę komputera hosta debugera  
  
1.  Na komputerze docelowym, otwórz **Start** menu wskaż **Akcesoria** a następnie kliknij przycisk **polecenia**.  
  
2.  W **polecenia** okna, typ:  
  
    ```cmd
    ping <debugger_host_computer_name>  
    ```  
  
3.  W pierwszym wierszu `ping` odpowiedzi zawiera pełną nazwę komputera i adres IP zwrócony przez serwer DNS dla określonego komputera.  
  
4.  Na komputerze-hoście debugera, otwarcie **polecenia** okna i uruchom `ipconfig`.  
  
5.  Porównaj wartości adresów IP.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
