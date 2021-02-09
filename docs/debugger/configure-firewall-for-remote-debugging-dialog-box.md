---
title: Okno dialogowe Konfigurowanie zapory dla zdalnego debugowania | Microsoft Docs
description: Przeczytaj informacje o oknie dialogowym Konfigurowanie zapory dla zdalnego debugowania, które pojawia się, gdy Zapora systemu Windows przestanie być odbierać dane przez sieć.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4fb1d704e2a06ed6c31d6b401b592436c86e4318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857730"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Konfigurowanie zapory do zdalnego debugowania — Okno dialogowe
To okno dialogowe pojawia się, gdy Zapora systemu Windows zablokuje dostęp do informacji za pośrednictwem sieci. Aby kontynuować debugowanie zdalne, musisz otworzyć otwór w zaporze, aby debuger mógł odbierać informacje.

> [!CAUTION]
> Otwarcie otworu w zaporze może narazić komputer na zagrożenia bezpieczeństwa, które jest przeznaczone do blokowania przez zaporę. Otwarcie otworu dla zdalnego debugowania odblokowuje porty 4020 i 4021 w programie Visual Studio 2015. W innych wersjach programu Visual Studio używane są inne numery portów. Aby uzyskać więcej informacji, zobacz [zdalne przydziały portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md). Ponadto umożliwia debugerowi otwieranie dodatkowych portów. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>Lista elementów UI
 **Anuluj debugowanie zdalne** Anuluje próbę debugowania zdalnego. Ustawienia zabezpieczeń na komputerze pozostają nienaruszone.

 **Odblokuj debugowanie zdalne z komputerów w sieci lokalnej (podsieci)** Włącza zdalne debugowanie maszyn w podsieci lokalnej. Może to spowodować otwarcie luk w zabezpieczeniach maszyn w podsieci lokalnej, ale Zapora nadal blokuje informacje pochodzące spoza podsieci.

 **Odblokuj debugowanie zdalne z dowolnego komputera** Umożliwia zdalne debugowanie maszyn w dowolnym miejscu w sieci. To ustawienie jest najmniej bezpieczne.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
- [Debugowanie odwołań do interfejsu użytkownika](../debugger/debugging-user-interface-reference.md)