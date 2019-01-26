---
title: Błędy punktu przerwania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea48e83034a02f4c99bb1d9de03db0ee1b371281
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038425"
---
# <a name="breakpoint-errors"></a>Błędy punktu przerwania
Poniżej opisano proces, gdy punkt przerwania podejmuje próbę powiązania do kodu, ale nie powiedzie się.  
  
## <a name="troubleshoot-a-breakpoint-error"></a>Rozwiązywanie problemów z Błąd punktu przerwania  
  
1.  Aparat debugowania (DE) wysyła [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do Menedżer debugowania sesji (SDM).  
  
2.  Wywołania SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) można pobrać błąd punktu przerwania.  
  
3.  Wywołania SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) można pobrać oczekujący punkt przerwania, z którego pochodzi błąd punktu przerwania.  
  
4.  Wywołania SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) można pobrać powód, dlaczego błąd punktu przerwania nie może utworzyć powiązania.  
  
## <a name="see-also"></a>Zobacz także  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)