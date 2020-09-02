---
title: Tworzenie punktu przerwania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cde6d660506e05195ef9f5c0825845cee10ae5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805481"
---
# <a name="creating-a-breakpoint"></a>Tworzenie punktu przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano proces tworzenia punktu przerwania.  
  
## <a name="methods-in-breakpoint-creation"></a>Metody w tworzeniu punktu przerwania  
 Gdy ładowany jest moduł, który jest wymagany do powiązania punktu przerwania, Menedżer debugowania sesji (SDM) wywołuje następujące metody:  
  
1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    > Element **rebind** jest wywoływany tylko wtedy, gdy użytkownik wykonuje punkt przerwania z okna punkty przerwania.  
  
4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
