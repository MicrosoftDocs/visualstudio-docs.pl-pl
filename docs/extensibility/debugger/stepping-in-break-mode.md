---
title: Krokowe przechodzenie w tryb przerwania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712857"
---
# <a name="stepping-in-break-mode"></a>Krokowe przechodzenie w tryb przerwania
W poniższej sekcji opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi przekroczyć kod:

## <a name="stepping-process"></a>Proces krokowe

1. Wywołaj [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) z argumentami [STEPKIND](../../extensibility/debugger/reference/stepkind.md) i [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) , aby wykonać krok.

2. Po zakończeniu kroku Wyślij [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako zdarzenie zatrzymujące.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
