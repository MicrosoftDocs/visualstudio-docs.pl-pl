---
title: 'Błąd: Upewnij się, że DNS jest prawidłowo skonfigurowany na komputerze docelowym | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
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
ms.openlocfilehash: 3b884326eb2e3aeeb03381088d0dc5b7caa07475
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923062"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Błąd: Upewnij się, że DNS jest prawidłowo skonfigurowany na komputerze docelowym
Podczas próby przeprowadzać debugowanie zdalne, może pojawić się następujący komunikat o błędzie:  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Ten błąd występuje, gdy komputer docelowy nie może rozpoznać nazwę komputera hosta debugera programu Visual Studio. Sprawdź ustawienia DNS na komputerze docelowym.  
  
- Aby uzyskać informacje dotyczące wyświetlania ustawień DNS w Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 lub Windows Server 2008 R2, w tym: na **Start** menu, wybierz **Pomoc i obsługa techniczna** , a następnie wyszukaj **Zmienianie ustawień protokołu TCP/IP**.  
  
- Aby uzyskać więcej informacji, przejdź do [witryny sieci web Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) i wyszukaj **Zmienianie ustawień protokołu TCP/IP**.  
  
  Jeśli nie możesz rozwiązać problem z systemem DNS, można spróbować uruchomić debugera zdalnego przy użyciu innego konta. Ten błąd występuje tylko wtedy, gdy uruchamiasz debuger zdalny systemu lokalnego lub konto Usługa sieciowa. Po uruchomieniu zdalnego debugera na innym koncie, może używać uwierzytelniania NTLM, które nie wymagają DNS. . Procedury można wyświetlić [błąd: Usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
