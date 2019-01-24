---
title: 'Błąd: Upewnij się, że DNS jest prawidłowo skonfigurowany na komputerze docelowym | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d23d13d5dfcd0dc0426f72ea87659fc0c85b323b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797523"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Błąd: Upewnij się, że DNS jest prawidłowo skonfigurowany na komputerze docelowym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas próby przeprowadzać debugowanie zdalne, może pojawić się następujący komunikat o błędzie:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Ten błąd występuje, gdy komputer docelowy nie może rozpoznać nazwę komputera hosta debugera programu Visual Studio. Sprawdź ustawienia DNS na komputerze docelowym.  
  
- Aby uzyskać informacje dotyczące wyświetlania ustawień DNS w Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 lub Windows Server 2008 R2, w tym: na **Start** menu, wybierz **Pomoc i obsługa techniczna** , a następnie wyszukaj **Zmienianie ustawień protokołu TCP/IP**.  
  
- Aby uzyskać więcej informacji, przejdź do [witryny sieci web Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) i wyszukaj **Zmienianie ustawień protokołu TCP/IP**.  
  
  Jeśli nie możesz rozwiązać problem z systemem DNS, można spróbować uruchomić debugera zdalnego przy użyciu innego konta. Ten błąd występuje tylko wtedy, gdy uruchamiasz debuger zdalny systemu lokalnego lub konto Usługa sieciowa. Po uruchomieniu zdalnego debugera na innym koncie, może używać uwierzytelniania NTLM, które nie wymagają DNS. . Procedury można wyświetlić [błąd: Usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
