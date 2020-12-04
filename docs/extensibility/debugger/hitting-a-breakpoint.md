---
title: Naciśnięcie punktu przerwania | Microsoft Docs
description: W tym artykule opisano proces, który ma miejsce, gdy silnik debugowania trafi w punkt przerwania podczas uruchamiania lub wykonywania kroków.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560853"
---
# <a name="hit-a-breakpoint"></a>Trafienie punktu przerwania
W poniższej sekcji opisano proces, w którym aparat debugowania (DE) trafi do punktu przerwania podczas uruchamiania lub wykonywania kroków:

## <a name="troubleshoot-a-hit-breakpoint"></a>Rozwiązywanie problemów z punktem przerwania trafień

1. Element DE wysyła Interfejs [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Menedżer debugowania sesji (SDM) wywołuje [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby uzyskać punkt przerwania, który został trafiony.

## <a name="see-also"></a>Zobacz także
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
