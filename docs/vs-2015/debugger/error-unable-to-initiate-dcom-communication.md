---
title: 'Błąd: Nie można zainicjować komunikacji DCOM | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fff1c56915fe4a06d66bdb08ce60219642933b1b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682528"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Błąd: Nie można zainicjować komunikacji DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wystąpił błąd modelu DCOM podczas próby komunikacji z komputerem zdalnym komputerze lokalnym. Jest to spowodowane przez zaporę na serwerze zdalnym lub uszkodzone uwierzytelniania Windows na komputerze zdalnym.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli maszyna zdalna ma włączoną zaporę Windows, zobacz [Ustaw się narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) instrukcje dotyczące sposobu konfigurowania zapory dla debugowania lokalnego.  
  
- Aby przywrócić uwierzytelniania Windows, spróbuj wykonać ponowny rozruch obu komputerach. Sprawdź dzienniki zdarzeń na komputerach lokalnych i zdalnych dla błędów protokołu Kerberos i skontaktuj się z administratorami domeny o znanych problemach.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
