---
title: Usuwanie punktu przerwania | Microsoft Docs
description: Dowiedz się, jak Menedżer debugowania sesji usuwa oczekujący punkt przerwania i wszystkie powiązane punkty przerwania powiązane z nim, gdy zostanie usunięty oczekujący punkt przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862178"
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
Poniżej opisano proces usuwania oczekujących punktów przerwania:

## <a name="deletion-process"></a>Proces usuwania
 Menedżer debugowania sesji (SDM) wywołuje metodę [IDebugPendingBreakpoint2::D](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) Usuń, aby usunąć oczekujący punkt przerwania i wszystkie powiązane z nim punkty przerwania.

> [!NOTE]
> Pojedynczy punkt przerwania powiązany może być również usunięty przez wywołanie [IDebugBoundBreakpoint2::D Usuń](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Zobacz też
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
