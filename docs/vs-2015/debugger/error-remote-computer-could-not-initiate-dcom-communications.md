---
title: 'Błąd: komputer zdalny nie może zainicjować komunikacji DCOM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8ddec2bdec09da1f1175b59c94db31841a1453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697335"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Błąd: Zdalny komputer nie mógł zainicjować komunikacji DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wystąpił błąd DCOM, gdy maszyna zdalna próbowała komunikować się z maszyną lokalną. Komputer lokalny jest maszyną, która jest  
  
 Uruchamianie programu Visual Studio. Ten błąd może wystąpić z kilku powodów:  
  
- Na komputerze lokalnym jest włączona Zapora.  
  
- Uwierzytelnianie systemu Windows z komputera zdalnego na komputerze lokalnym nie działa.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Jeśli na komputerze lokalnym jest włączona Zapora systemu Windows, zobacz [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) , aby uzyskać instrukcje dotyczące sposobu konfigurowania zapory na potrzeby debugowania lokalnego.  
  
2. Przetestuj uwierzytelnianie systemu Windows, próbując otworzyć udział plików na komputerze lokalnym z serwera zdalnego.  
  
3. Aby przywrócić uwierzytelnianie systemu Windows, spróbuj ponownie uruchomić obie maszyny. Należy przejrzeć dzienniki zdarzeń na maszynach lokalnych i zdalnych pod kątem błędów protokołu Kerberos i skontaktować się z administratorami domeny w poszukiwaniu znanych problemów.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
