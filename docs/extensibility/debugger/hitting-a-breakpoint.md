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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 808bf95631bb4106d071c29d7af233d071ef5229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947726"
---
# <a name="hit-a-breakpoint"></a>Trafienie punktu przerwania
W poniższej sekcji opisano proces, w którym aparat debugowania (DE) trafi do punktu przerwania podczas uruchamiania lub wykonywania kroków:

## <a name="troubleshoot-a-hit-breakpoint"></a>Rozwiązywanie problemów z punktem przerwania trafień

1. Element DE wysyła Interfejs [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.

2. Menedżer debugowania sesji (SDM) wywołuje [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby uzyskać punkt przerwania, który został trafiony.

## <a name="see-also"></a>Zobacz też
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
