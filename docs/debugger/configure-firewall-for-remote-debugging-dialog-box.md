---
title: Konfigurowanie zapory dla zdalnego debugowania okno dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a7346d9398ab9743319661efffdaf3f1f4b89b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018608"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Konfigurowanie zapory do zdalnego debugowania — Okno dialogowe
To okno dialogowe pojawia się, gdy Zapora Windows zablokuje debugera na odbieranie informacji za pośrednictwem sieci. Aby kontynuować, zdalne debugowanie, możesz otworzyć dziury w zaporze aby debuger może odbierać informacje.  
  
> [!CAUTION]
>  Otwieranie dziury w zaporze może narazić komputer na zagrożenia, które Zapora jest przeznaczony do blokowania zabezpieczeń. Otwieranie dziury dla zdalnego debugowania odblokowuje porty 4020 i 4021 w programie Visual Studio 2015. W innych wersjach programu Visual Studio używane są inne numery portów. Aby uzyskać więcej informacji, zobacz [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md). Ponadto umożliwia debugera, otwarcie dodatkowych portów. Aby uzyskać więcej informacji, zobacz [skonfigurować zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Anuluj debugowanie zdalne**  
 Anuluje próby zdalnego debugowania. Ustawienia zabezpieczeń komputera pozostają bez zmian.  
  
 **Odblokuj debugowanie zdalne z komputerami w sieci lokalnej (podsieci)**  
 Umożliwia zdalne debugowanie maszyn w podsieci lokalnej. To może być otwarcie luk w zabezpieczeniach do komputerów w podsieci lokalnej, ale zapory w dalszym ciągu Blokuj informacje pochodzące spoza tej podsieci.  
  
 **Odblokuj debugowanie zdalne z dowolnego komputera**  
 Umożliwia zdalne debugowanie maszyn w dowolnym miejscu w sieci. To ustawienie jest najniższy poziom zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)  
 [Debugowanie odwołań do interfejsu użytkownika](../debugger/debugging-user-interface-reference.md)