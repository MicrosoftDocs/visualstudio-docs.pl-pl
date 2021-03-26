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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1d8e0d68f32ece7760805c05fd281b0e62a70003
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097282"
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
Poniżej opisano proces usuwania oczekujących punktów przerwania:

## <a name="deletion-process"></a>Proces usuwania
 Menedżer debugowania sesji (SDM) wywołuje metodę [IDebugPendingBreakpoint2::D](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) Usuń, aby usunąć oczekujący punkt przerwania i wszystkie powiązane z nim punkty przerwania.

> [!NOTE]
> Pojedynczy punkt przerwania powiązany może być również usunięty przez wywołanie [IDebugBoundBreakpoint2::D Usuń](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Zobacz też
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
