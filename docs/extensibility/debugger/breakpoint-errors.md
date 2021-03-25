---
title: Błędy punktu przerwania | Microsoft Docs
description: Dowiedz się więcej o procesie, gdy punkt przerwania próbuje powiązać się z kodem, ale kończy się niepowodzeniem i sposobem rozwiązywania problemów z punktem przerwania
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12e8efc7fc110f3f5c20c92d97cf3692094ef6aa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055244"
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
