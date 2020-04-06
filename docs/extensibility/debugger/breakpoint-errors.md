---
title: Błędy punktu przerwania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739218"
---
# <a name="breakpoint-errors"></a>Błędy punktu przerwania
Poniżej opisano proces, gdy punkt przerwania próbuje powiązać z kodem, ale kończy się niepowodzeniem.

## <a name="troubleshoot-a-breakpoint-error"></a>Rozwiązywanie problemów z błędem punktu przerwania

1. Aparat debugowania (DE) wysyła [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do menedżera debugowania sesji (SDM).

2. SDM wywołuje [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2** `ppErrorBP`), aby uzyskać punkt przerwania błędu.

3. SDM wywołuje [IDebugErrorBreakpoint2::GetPendingBreakpoint,](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) aby uzyskać oczekujących breakpoint, z którego pochodzi punkt przerwania błędu.

4. SDM wywołuje [IDebugErrorBreakpoint2::GetBreakpointResolution,](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) aby uzyskać przyczynę, dla którego punkt przerwania błędu nie może powiązać.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
