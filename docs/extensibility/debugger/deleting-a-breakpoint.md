---
title: Usuwanie punktu przerwania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738952"
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
Poniżej opisano proces usuwania oczekujących punktów przerwania:

## <a name="deletion-process"></a>Proces usuwania
 Menedżer debugowania sesji (SDM) wywołuje metodę [IDebugPendingBreakpoint2::D](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) Usuń, aby usunąć oczekujący punkt przerwania i wszystkie powiązane z nim punkty przerwania.

> [!NOTE]
> Pojedynczy punkt przerwania powiązany może być również usunięty przez wywołanie [IDebugBoundBreakpoint2::D Usuń](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Zobacz też
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
