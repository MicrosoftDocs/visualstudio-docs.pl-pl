---
title: Aktywacja punktu przerwania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d95abd66f248ca994d7712f1bf51519022de9d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344048"
---
# <a name="hit-a-breakpoint"></a>Trafiony punkt przerwania
W poniższej sekcji opisano proces, gdy aparat debugowania (DE) trafienia punktu przerwania podczas uruchamiania lub przechodzenie krok po kroku:

## <a name="troubleshoot-a-hit-breakpoint"></a>Rozwiązywanie problemów z trafień punktu przerwania

1. Wysyła DE [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfejsu jako **EVENT_SYNC_STOP**.

2. Menedżer debugowania sesji (SDM) wywołuje [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) można pobrać punkcie przerwania, który został trafiony.

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)