---
title: Naciśnięcie punktu przerwania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738566"
---
# <a name="hit-a-breakpoint"></a>Trafienie punktu przerwania
W poniższej sekcji opisano proces, w którym aparat debugowania (DE) trafi do punktu przerwania podczas uruchamiania lub wykonywania kroków:

## <a name="troubleshoot-a-hit-breakpoint"></a>Rozwiązywanie problemów z punktem przerwania trafień

1. Element DE wysyła Interfejs [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Menedżer debugowania sesji (SDM) wywołuje [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby uzyskać punkt przerwania, który został trafiony.

## <a name="see-also"></a>Zobacz też
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
