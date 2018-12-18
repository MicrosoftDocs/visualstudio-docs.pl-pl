---
title: Konfigurowanie zapory dla zdalnego debugowania okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: c899de05321ee8c6579b9dbbdb35befa0b97d2b3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762073"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Konfigurowanie zapory do zdalnego debugowania — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Konfigurowanie narzędzi zdalnych na urządzeniu](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Debugowanie odwołań do interfejsu użytkownika](../debugger/debugging-user-interface-reference.md)



