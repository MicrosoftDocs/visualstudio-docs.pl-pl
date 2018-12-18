---
title: Uruchamianie debugera | Dokumentacja firmy Microsoft
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
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bcb73a46f6055d1c8637fe1d5375ba9be0fc8652
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774877"
---
# <a name="launching-the-debugger"></a>Uruchamianie debugera
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uruchamianie debugera wymaga wysyłania odpowiedniej kolejności metod i zdarzeń za pomocą ich odpowiednich atrybutów.  
  
## <a name="sequences-of-methods-and-events"></a>Sekwencje metody i zdarzenia  
  
1.  Menedżer debugowania sesji (SDM) nosi nazwę, wybierając **debugowania** menu, a następnie wybierając **Start**. Zobacz [uruchamianie programu](../../extensibility/debugger/launching-a-program.md) Aby uzyskać więcej informacji.  
  
2.  Wywołania SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.  
  
3.  Na podstawie modelu procesu aparatu (DE) debugowania, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca jedną z następujących metod, które określa, co dzieje się potem.  
  
     Jeśli `S_FALSE` ma zostać zwrócona, aparat debugowania (DE) ma zostać załadowany w trakcie maszyny wirtualnej.  
  
     —lub—  
  
     Jeśli `S_OK` ma zostać zwrócona, DE ma być załadowany w procesie programu SDM. SDM następnie wykonuje następujące zadania:  
  
    1.  Wywołania [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) można pobrać informacji o aparacie programu DE.  
  
    2.  Wspólnie tworzy DE.  
  
    3.  Wywołania [dołączyć](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Wysyła DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
5.  Wysyła DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
6.  Wysyła DE [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
7.  Wysyła DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
8.  Wysyła DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)   
 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)

