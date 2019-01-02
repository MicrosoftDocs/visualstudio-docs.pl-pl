---
title: 'Błąd: Nie można nawiązać połączenia z maszyną &lt;nazwa&gt;. Nie można odnaleźć maszyny w sieci. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4c9bc3c72a2ff97fc67f31f44041feed2185551
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847376"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Błąd: Nie można nawiązać połączenia z maszyną &lt;nazwa&gt;. Nie można odnaleźć maszyny w sieci.
Dzieje się tak, jeśli jest spełniony jeden z następujących warunków:  
  
-   Połączenie z komputerem zdalnym zostało przerwane.  
  
-   Twoje konto użytkownika na komputerze zdalnym jest wyłączone.  
  
-   Wygasło hasło na komputerze zdalnym.  
  
### <a name="to-resolve-this-behavior"></a>Aby rozwiązać ten problem  
  
-   Upewnij się, że komputer lokalny i komputer zdalny znajdują się w tej samej sieci. Aby to zrobić, należy użyć Eksplorator systemu Microsoft Windows (lub Eksploratora plików), aby spróbować uzyskać dostęp do komputera zdalnego.  
  
     — i —  
  
-   Upewnij się, że konto użytkownika, którego używasz, aby nawiązać połączenie z komputerem zdalnym jest włączona.  
  
     — i —  
  
-   Upewnij się, że hasło, którego używasz do podłączenia do komputera zdalnego jest prawidłowy i nie wygasł.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)