---
title: 'Błąd: nie można zainicjować komunikacji DCOM | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682528"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Błąd: nie można zainicjować komunikacji DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wystąpił błąd DCOM, gdy komputer lokalny próbował się skomunikować z maszyną zdalną. Jest to spowodowane przez zaporę na serwerze zdalnym lub uszkodzenie uwierzytelniania systemu Windows na maszynie zdalnej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli na komputerze zdalnym jest włączona Zapora systemu Windows, zobacz [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) , aby uzyskać instrukcje dotyczące sposobu konfigurowania zapory na potrzeby debugowania lokalnego.  
  
- Aby przywrócić uwierzytelnianie systemu Windows, spróbuj ponownie uruchomić obie maszyny. Należy przejrzeć dzienniki zdarzeń na maszynach lokalnych i zdalnych pod kątem błędów protokołu Kerberos i skontaktować się z administratorami domeny w poszukiwaniu znanych problemów.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
