---
title: Wykonywanie krokowe w trybie przerwania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065925"
---
# <a name="stepping-in-break-mode"></a>Wykonywanie krokowe w trybie przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano proces, który występuje, gdy debuger jest w trybie przerwania, a także musi przejść przez kod:  
  
## <a name="stepping-process"></a>Proces przechodzenia krok po kroku  
  
1. Wywołaj [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) z [STEPKIND](../../extensibility/debugger/reference/stepkind.md) i [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumenty, które można wykonać kroku.  
  
2. Po zakończeniu kroku wysyłania [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako zdarzenie zatrzymywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
