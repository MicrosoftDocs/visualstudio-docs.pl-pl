---
title: Wykonywanie krokowe w trybie przerwania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3a8688f32a97d27ee6f6e2d18fcea8e25feaac2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348544"
---
# <a name="stepping-in-break-mode"></a>Wykonywanie krokowe w trybie przerwania
W poniższej sekcji opisano proces, który występuje, gdy debuger jest w trybie przerwania, a także musi przejść przez kod:

## <a name="stepping-process"></a>Proces przechodzenia krok po kroku

1. Wywołaj [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) z [STEPKIND](../../extensibility/debugger/reference/stepkind.md) i [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumenty, które można wykonać kroku.

2. Po zakończeniu kroku wysyłania [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako zdarzenie zatrzymywania.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)