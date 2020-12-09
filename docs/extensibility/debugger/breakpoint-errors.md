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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a5003ce8abe79fcba9f9604047d2265810fda2
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914494"
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
