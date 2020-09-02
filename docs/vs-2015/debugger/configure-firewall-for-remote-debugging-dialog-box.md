---
title: Okno dialogowe Konfigurowanie zapory dla zdalnego debugowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e2b1300feb8d2a15e63089ee9bddde5f2d1ef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702284"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Konfigurowanie zapory do zdalnego debugowania — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe pojawia się, gdy Zapora systemu Windows zablokuje dostęp do informacji za pośrednictwem sieci. Aby kontynuować debugowanie zdalne, musisz otworzyć otwór w zaporze, aby debuger mógł odbierać informacje.  
  
> [!CAUTION]
> Otwarcie otworu w zaporze może narazić komputer na zagrożenia bezpieczeństwa, które jest przeznaczone do blokowania przez zaporę. Otwarcie otworu dla zdalnego debugowania odblokowuje porty 4020 i 4021 w programie Visual Studio 2015. W innych wersjach programu Visual Studio używane są inne numery portów. Aby uzyskać więcej informacji, zobacz [zdalne przydziały portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Ponadto umożliwia debugerowi otwieranie dodatkowych portów. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Anuluj debugowanie zdalne**  
 Anuluje próbę debugowania zdalnego. Ustawienia zabezpieczeń na komputerze pozostają nienaruszone.  
  
 **Odblokuj debugowanie zdalne z komputerów w sieci lokalnej (podsieci)**  
 Włącza zdalne debugowanie maszyn w podsieci lokalnej. Może to spowodować otwarcie luk w zabezpieczeniach maszyn w podsieci lokalnej, ale Zapora nadal blokuje informacje pochodzące spoza podsieci.  
  
 **Odblokuj debugowanie zdalne z dowolnego komputera**  
 Umożliwia zdalne debugowanie maszyn w dowolnym miejscu w sieci. To ustawienie jest najmniej bezpieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Debugowanie odwołań do interfejsu użytkownika](../debugger/debugging-user-interface-reference.md)
