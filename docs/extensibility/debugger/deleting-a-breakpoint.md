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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061175326a19af1866262421b381eb14267c7efd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915560"
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
Poniżej opisano proces usuwania oczekujących punktów przerwania:

## <a name="deletion-process"></a>Proces usuwania
 Menedżer debugowania sesji (SDM) wywołuje metodę [IDebugPendingBreakpoint2::D](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) Usuń, aby usunąć oczekujący punkt przerwania i wszystkie powiązane z nim punkty przerwania.

> [!NOTE]
> Pojedynczy punkt przerwania powiązany może być również usunięty przez wywołanie [IDebugBoundBreakpoint2::D Usuń](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Zobacz też
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
