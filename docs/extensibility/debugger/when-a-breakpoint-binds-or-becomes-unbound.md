---
title: Gdy punkt przerwania tworzy powiązanie lub zostaje niepowiązany | Microsoft Docs
description: Poznaj niepowiązane punkty przerwania. Gdy punkt przerwania nie może być powiązany w czasie wywołania, czas powiązania i czas utworzenia punktu przerwania są różne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6e1a6acdee89be293ab4a6dc72a3d4fd4336d88
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091412"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Gdy punkt przerwania tworzy powiązanie lub zostaje niepowiązany
Gdy punkt przerwania nie może być powiązany w momencie wywołania metody [IDebugPendingBreakpoint2:: NOBIND](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , czas powiązania i czas utworzenia punktu przerwania są różne.

## <a name="methods-called"></a>Metody wywoływane
 Menedżer debugowania sesji (SDM) wywołuje następujące metody:

1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). Funkcja DE zwraca element [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2:: Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2:: Wirtualizacja](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. Metoda [IDebugPendingBreakpoint2:: bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) i zwraca S_OK. Po wysłaniu elementu [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) lub [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) i [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) metody do weryfikacji i uzyskiwania powiązanych punktów przerwania.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
