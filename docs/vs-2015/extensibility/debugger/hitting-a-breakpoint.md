---
title: Naciśnięcie punktu przerwania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152694"
---
# <a name="hitting-a-breakpoint"></a>Aktywacja punktu przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano proces, w którym aparat debugowania (DE) trafi do punktu przerwania podczas uruchamiania lub wykonywania kroków:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Rozwiązywanie problemów z punktem przerwania trafień  
  
1. Element DE wysyła Interfejs [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) jako **EVENT_SYNC_STOP**.  
  
2. Menedżer debugowania sesji (SDM) wywołuje [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , aby uzyskać punkt przerwania, który został trafiony.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
