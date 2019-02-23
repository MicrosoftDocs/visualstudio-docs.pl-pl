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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22cada0aaf77edd241992229c2bd6733be3ccc81
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711166"
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
Poniżej przedstawiono ten proces, podczas usuwania oczekujący punkt przerwania:

## <a name="deletion-process"></a>Proces usuwania
 Menedżer debugowania sesji (SDM) wywołuje [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodę, aby usunąć oczekujący punkt przerwania i wszystkie powiązane punkty przerwania powiązany z niego.

> [!NOTE]
>  Pojedynczy powiązany punkt przerwania mogą być również usuwane przez wywołanie [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)