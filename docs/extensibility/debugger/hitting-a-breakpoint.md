---
title: Trafienie w punkt przerwania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738566"
---
# <a name="hit-a-breakpoint"></a>Trafienie w punkt przerwania
W poniższej sekcji opisano proces, gdy aparat debugowania (DE) uderza punkt przerwania podczas pracy lub stepping:

## <a name="troubleshoot-a-hit-breakpoint"></a>Rozwiązywanie problemów z punktem przerwania trafienia

1. DE wysyła interfejs [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Menedżer debugowania sesji (SDM) wywołuje [IDebugBreakpointEvent2:::EnumBreakpoints,](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) aby uzyskać punkt przerwania, który został trafiony.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
