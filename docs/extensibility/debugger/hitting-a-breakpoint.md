---
title: Aktywacja punktu przerwania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1286af8222703028d5a8a1bd2dbb0d990ca7e30c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041096"
---
# <a name="hit-a-breakpoint"></a>Trafiony punkt przerwania
W poniższej sekcji opisano proces, gdy aparat debugowania (DE) trafienia punktu przerwania podczas uruchamiania lub przechodzenie krok po kroku:

## <a name="troubleshoot-a-hit-breakpoint"></a>Rozwiązywanie problemów z trafień punktu przerwania

1. Wysyła DE [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfejsu jako **EVENT_SYNC_STOP**.

2. Menedżer debugowania sesji (SDM) wywołuje [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) można pobrać punkcie przerwania, który został trafiony.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)