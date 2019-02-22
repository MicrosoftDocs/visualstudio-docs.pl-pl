---
title: Wykonywanie krokowe w trybie przerwania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66e7e227daa0dd58bf24ae946cce667992e09f90
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685030"
---
# <a name="stepping-in-break-mode"></a>Wykonywanie krokowe w trybie przerwania
W poniższej sekcji opisano proces, który występuje, gdy debuger jest w trybie przerwania, a także musi przejść przez kod:

## <a name="stepping-process"></a>Proces przechodzenia krok po kroku

1.  Wywołaj [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) z [STEPKIND](../../extensibility/debugger/reference/stepkind.md) i [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumenty, które można wykonać kroku.

2.  Po zakończeniu kroku wysyłania [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako zdarzenie zatrzymywania.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)