---
title: 'Błąd: Upewnij się, że serwer DNS jest prawidłowo skonfigurowany na komputerze docelowym | Microsoft Docs'
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
ms.openlocfilehash: 35c258a018bec8bd38f8b43690c18b37ee9d6c39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851933"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Błąd: upewnij się, że DNS jest prawidłowo skonfigurowany na komputerze docelowym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas próby debugowania zdalnego może zostać wyświetlony następujący komunikat o błędzie:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Ten błąd występuje, gdy komputer docelowy nie może rozpoznać nazwy komputera hosta debugera programu Visual Studio. Sprawdź ustawienia DNS na komputerze docelowym.  
  
- Aby uzyskać informacje o wyświetlaniu ustawienia DNS w Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 lub Windows Server 2008 R2, wykonaj następujące czynności: w menu **Start** wybierz polecenie **Pomoc i obsługa techniczna**, a następnie wyszukaj pozycję **Zmień ustawienia protokołu TCP/IP**.  
  
- Aby uzyskać więcej informacji, przejdź do [witryny sieci Web systemu Microsoft Windows](https://windows.microsoft.com/) i Wyszukaj pozycję **Zmień ustawienia protokołu TCP/IP**.  
  
  Jeśli nie możesz rozwiązać problemu z usługą DNS, możesz spróbować uruchomić zdalny debuger przy użyciu innego konta. Ten błąd występuje tylko w przypadku uruchamiania zdalnego debugera w ramach konta System lokalny lub usługa sieciowa. W przypadku uruchomienia zdalnego debugera w ramach innego konta może on korzystać z uwierzytelniania NTLM, które nie wymaga usługi DNS. . Aby uzyskać procedurę, zobacz [błąd: usługa zdalny debuger programu Visual Studio na komputerze docelowym nie może nawiązać połączenia z powrotem z tym komputerem](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
