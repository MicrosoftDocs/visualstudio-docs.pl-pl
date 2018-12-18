---
title: Usuwanie punktu przerwania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b53be5e09d4579d95cb4b9d9726d6087effb8ff1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797393"
---
# <a name="deleting-a-breakpoint"></a>Usuwanie punktu przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej przedstawiono ten proces, podczas usuwania oczekujący punkt przerwania:  
  
## <a name="deletion-process"></a>Proces usuwania  
 Menedżer debugowania sesji (SDM) wywołuje [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodę, aby usunąć oczekujący punkt przerwania i wszystkie powiązane punkty przerwania powiązany z niego.  
  
> [!NOTE]
>  Pojedynczy powiązany punkt przerwania mogą być również usuwane przez wywołanie [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)

