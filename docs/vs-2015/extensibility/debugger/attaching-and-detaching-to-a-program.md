---
title: Dołączanie i odłączanie programu | Dokumentacja firmy Microsoft
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
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b6bba6600d3ea32073a908199f5cd6ddaa33ef9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762799"
---
# <a name="attaching-and-detaching-to-a-program"></a>Dołączanie do programu i odłączanie od niego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dołączanie debugera wymaga wysyłania odpowiedniej kolejności metod i zdarzeń z odpowiednich atrybutów.  
  
## <a name="sequence-of-methods-and-events"></a>Sekwencja metody i zdarzenia  
  
1. Menedżer debugowania sesji (SDM) wywołuje [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.  
  
    Na podstawie modelu procesu aparatu (DE) debugowania, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca jedną z następujących metod, które określa, co dzieje się potem.  
  
    Jeśli `S_FALSE` ma zostać zwrócona, aparat debugowania pomyślnie został dołączony do programu. W przeciwnym razie [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md) metoda jest wywoływana w celu ukończenia procesu dołączania.  
  
    Jeśli `S_OK` ma zostać zwrócona, Niemcy, które ma być ładowane w tym samym procesie co SDM. SDM wykonuje następujące zadania:  
  
   1.  Wywołania [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) można pobrać informacji o aparacie programu DE.  
  
   2.  Wspólnie tworzy DE.  
  
   3.  Wywołania [dołączyć](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2. Wysyła DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
3. Wysyła DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
4. Wysyła DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM z `EVENT_SYNC_STOP` atrybutu.  
  
   Odłączanie programu jest proste, dwuetapowy proces:  
  
5. Wywołania SDM [Odłącz](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
6. Wysyła DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)

