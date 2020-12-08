---
title: Krokowe przechodzenie w tryb przerwania | Microsoft Docs
description: Dowiedz się więcej o procesie, który występuje, gdy debuger jest w trybie przerwania. Debuger musi następnie przejść przez kod.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 80273bf470a3ed0c342e781085de6e991508451c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845196"
---
# <a name="stepping-in-break-mode"></a>Krokowe przechodzenie w tryb przerwania
W poniższej sekcji opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi przekroczyć kod:

## <a name="stepping-process"></a>Proces krokowe

1. Wywołaj [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) z argumentami [STEPKIND](../../extensibility/debugger/reference/stepkind.md) i [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) , aby wykonać krok.

2. Po zakończeniu kroku Wyślij [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako zdarzenie zatrzymujące.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
