---
title: Usuwanie punktu przerwania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b63fa7622b7dea4a6ad5c516547518911110a8ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958043"
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
Poniżej przedstawiono ten proces, podczas usuwania oczekujący punkt przerwania:  
  
## <a name="deletion-process"></a>Proces usuwania  
 Menedżer debugowania sesji (SDM) wywołuje [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodę, aby usunąć oczekujący punkt przerwania i wszystkie powiązane punkty przerwania powiązany z niego.  
  
> [!NOTE]
>  Pojedynczy powiązany punkt przerwania mogą być również usuwane przez wywołanie [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)