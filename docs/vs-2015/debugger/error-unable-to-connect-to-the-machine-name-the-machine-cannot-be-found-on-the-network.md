---
title: 'Błąd: nie można nawiązać połączenia z &lt; nazwą komputera &gt; . Nie można odnaleźć maszyny w sieci. | Microsoft Docs'
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
ms.openlocfilehash: dd1402a476ce2dceaaaf78580b36db20c3eed24f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682559"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Błąd: nie można nawiązać połączenia z &lt; nazwą komputera &gt; . Nie można odnaleźć maszyny w sieci.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Takie zachowanie występuje, gdy spełniony jest jeden z następujących warunków:  
  
- Połączenie z komputerem zdalnym zostało przerwane.  
  
- Twoje konto użytkownika na komputerze zdalnym jest wyłączone.  
  
- Hasło na komputerze zdalnym wygasło.  
  
### <a name="to-resolve-this-behavior"></a>Aby rozwiązać ten problem  
  
- Upewnij się, że komputer lokalny i komputer zdalny znajdują się w tej samej sieci. Aby to zrobić, użyj Eksploratora Microsoft Windows (lub Eksploratora plików), aby spróbować uzyskać dostęp do komputera zdalnego.  
  
     lub  
  
- Upewnij się, że konto użytkownika używane do nawiązywania połączenia z komputerem zdalnym jest włączone.  
  
     lub  
  
- Upewnij się, że hasło używane do nawiązania połączenia z komputerem zdalnym jest prawidłowe i nie wygasło.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
