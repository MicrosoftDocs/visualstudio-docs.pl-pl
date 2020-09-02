---
title: Okno dialogowe Zatrzymaj debugowanie w toku | Microsoft Docs
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
ms.openlocfilehash: 4fc4b72987be726ab06aeb92a0e3eec2a338949e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684951"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Zatrzymanie trwającego debugowania — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To okno dialogowe pojawia się, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywanie sesji może zająć trochę czasu. Zatrzymywanie sesji debugowania jest zwykle bardzo szybkie i to okno dialogowe nie pojawia się. Czasami jednak odłączenie od wszystkich debugowanych procesów trwa dłużej. Jeśli zatrzymywanie sesji trwa dłużej niż kilka sekund (lub jeśli wystąpi błąd odłączenia), pojawi się to okno dialogowe. Jeśli taka sytuacja występuje często, może to być spowodowane problemem wewnętrznym i warto skontaktować się z pomocą techniczną.  
  
 Możesz poczekać, aż procesy zostaną odłączone, a to okno dialogowe zniknie lub użyj przycisku **Zatrzymaj teraz** , aby wymusić natychmiastowe zakończenie.  
  
 **Zatrzymaj teraz**  
 Kliknij ten przycisk, aby natychmiast zakończyć sesję debugowania. Użycie polecenia **Zatrzymaj teraz**zakończy się zamiast odłączania debugowanych procesów. Jeśli debugujesz procesy systemowe, zakończenie tych procesów z opcją **Zatrzymaj teraz** może mieć nieoczekiwane i niepożądane skutki.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Odłączanie programów](https://msdn.microsoft.com/f2c756c2-8079-474b-94c2-01c19a141a01)
