---
title: Uruchamianie debugera | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d1c1ba42d1d05217eff6e8ff7a0b6f1209a05db
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990886"
---
# <a name="launch-the-debugger"></a>Uruchamianie debugera
Uruchamianie debugera wymaga wysyłania odpowiedniej kolejności metod i zdarzeń za pomocą ich odpowiednich atrybutów.  
  
## <a name="sequences-of-methods-and-events"></a>Sekwencje metody i zdarzenia  
  
1.  Menedżer debugowania sesji (SDM) nosi nazwę, wybierając **debugowania** menu, a następnie wybierając **Start**. Aby uzyskać więcej informacji, zobacz [Uruchom program](../../extensibility/debugger/launching-a-program.md).  
  
2.  Wywołania SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.  
  
3.  Na podstawie modelu procesu aparatu (DE) debugowania, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca jedną z następujących metod, które określa, co dzieje się potem.  
  
     Jeśli `S_FALSE` zwraca, aparat debugowania (DE) ma zostać załadowany w trakcie maszyny wirtualnej.  
  
     —lub—  
  
     Jeśli `S_OK` zwraca, DE ma być załadowany w procesie programu SDM. SDM następnie wykonuje następujące zadania:  
  
    1.  Wywołania [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) można pobrać informacji o aparacie programu DE.  
  
    2.  Wspólnie tworzy DE.  
  
    3.  Wywołania [dołączyć](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Wysyła DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
5.  Wysyła DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
6.  Wysyła DE [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
7.  Wysyła DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
8.  Wysyła DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
## <a name="see-also"></a>Zobacz także  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)   
 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)