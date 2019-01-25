---
title: Zatrzymywanie debugowania w okno dialogowe postępu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.stopnow
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c29754937d3b1ff7f4c44fc87929d84844743387
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788123"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Zatrzymanie trwającego debugowania — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe pojawia się, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywania sesji jest zamierza zająć trochę czasu. Zatrzymywanie sesji debugowania jest zazwyczaj bardzo szybkie i nie ma tego okna dialogowego. Czasami jednak zajmuje dodatkowy czas, aby odłączyć od wszystkich procesów, które są debugowane. Jeśli zatrzymywania sesji przyjmuje więcej niż kilku sekund (lub jeśli wystąpi błąd odłączania), pojawi się okno dialogowe. W takim przypadku często, może to być spowodowane problem wewnętrzny i chcesz się z pomocą techniczną.  
  
 Poczekaj, aż procesy, które można odłączyć i to okno dialogowe zniknięcie lub użyj **Zatrzymaj** przycisk, aby wymusić natychmiastowe przerwanie działania.  
  
 **Zatrzymaj teraz**  
 Kliknij ten przycisk, aby zakończyć sesję debugowania natychmiast. Za pomocą **Zatrzymaj**spowoduje przerwanie działania, a nie Odłączanie procesów debugowania. Jeśli debugujesz procesy systemowe zakończenie tych procesów za pomocą **Zatrzymaj** może mieć niepożądane i nieoczekiwane skutki.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Trwa odłączanie programy](http://msdn.microsoft.com/f2c756c2-8079-474b-94c2-01c19a141a01)
