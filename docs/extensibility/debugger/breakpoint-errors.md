---
title: Błędy punktu przerwania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739218"
---
# <a name="breakpoint-errors"></a>Błędy punktów przerwania
Poniżej opisano proces, w którym punkt przerwania próbuje powiązać się z kodem, ale kończy się niepowodzeniem.

## <a name="troubleshoot-a-breakpoint-error"></a>Rozwiązywanie problemów z błędem punktu przerwania

1. Aparat debugowania (DE) wysyła [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do Menedżera debugowania sesji (SDM).

2. W przypadku wywołań modelu SDM [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ), aby uzyskać błąd punktu przerwania.

3. Model SDM wywołuje [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) , aby uzyskać oczekujący punkt przerwania, z którego pochodzi punkt przerwania błędu.

4. Model SDM wywołuje [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) , aby uzyskać powód, dla którego nie powiodło się powiązanie punktu przerwania błędu.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
