---
title: Zatrzymywanie debugowania w okno dialogowe postępu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3b2a3382fe9ac11f07d7fa9ebc5c1bc094cd526
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902507"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Zatrzymanie trwającego debugowania — Okno dialogowe
To okno dialogowe pojawia się, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywania sesji jest zamierza zająć trochę czasu. Zatrzymywanie sesji debugowania jest zazwyczaj bardzo szybkie i nie ma tego okna dialogowego. Czasami jednak zajmuje dodatkowy czas, aby odłączyć od wszystkich procesów, które są debugowane. Jeśli zatrzymywania sesji przyjmuje więcej niż kilku sekund (lub jeśli wystąpi błąd odłączania), pojawi się okno dialogowe. W takim przypadku często, może to być spowodowane problem wewnętrzny i chcesz się z pomocą techniczną.

 Poczekaj, aż procesy, które można odłączyć i to okno dialogowe zniknięcie lub użyj **Zatrzymaj** przycisk, aby wymusić natychmiastowe przerwanie działania.

 **Zatrzymaj teraz** kliknij ten przycisk, aby zakończyć sesję debugowania natychmiast. Za pomocą **Zatrzymaj** spowoduje przerwanie działania, a nie Odłączanie procesów debugowania. Jeśli debugujesz procesy systemowe zakończenie tych procesów za pomocą **Zatrzymaj** może mieć niepożądane i nieoczekiwane skutki.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Trwa odłączanie programy](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))