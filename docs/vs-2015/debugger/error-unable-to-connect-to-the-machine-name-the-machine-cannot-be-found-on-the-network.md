---
title: 'Błąd: Nie można nawiązać połączenia z maszyną &lt;nazwa&gt;. Nie można odnaleźć maszyny w sieci. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 151025ceb36715c1ac3269c5cfd55eba14685c8c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752364"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Błąd: Nie można nawiązać połączenia z maszyną &lt;nazwa&gt;. Nie można odnaleźć maszyny w sieci.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Konfigurowanie narzędzi zdalnych na urządzeniu](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
