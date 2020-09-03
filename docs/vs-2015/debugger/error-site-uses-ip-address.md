---
title: 'Błąd: witryna używa adresu IP | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46eace1c566a2810c5914a49654f8393f425fdee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155751"
---
# <a name="error-site-uses-ip-address"></a>Błąd: witryna korzysta z adresu IP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje, gdy debuger próbuje automatycznie dołączyć do aplikacji sieci Web, która korzysta z adresu IP. Dzieje się tak, jeśli zmienisz **tożsamość witryny sieci Web** tak, aby **używała określonego adresu IP** w usługach IIS.  
  
 Aby automatycznie dołączyć do pracy, musisz utworzyć projekt z określonym adresem IP, a nie tylko nazwą komputera. W przeciwnym razie debuger zmieni nazwę komputera na localhost, co spowoduje niepowodzenie wysłania zlecenia debugowania do usług IIS.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zamiast tego użyj opcji dołączania ręcznego (z menu Debuguj wybierz **Dołącz do procesu**).  
  
     —lub—  
  
2. Zmień ustawienie **identyfikacji witryny sieci Web usług IIS** .  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
