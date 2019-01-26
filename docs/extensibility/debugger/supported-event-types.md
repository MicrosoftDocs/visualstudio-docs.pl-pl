---
title: Obsługiwane typy zdarzeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d272ae5499d28b0290d45947b35bf6e7f7f41b8c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952254"
---
# <a name="supported-event-types"></a>Obsługiwane typy zdarzeń
Debugowanie programu Visual Studio obsługuje obecnie następujące typy zdarzeń:  
  
- Zdarzenia asynchroniczne  
  
   Powiadom Menedżer debugowania sesji (SDM) i środowisko IDE, który zmienia stan debugowanej aplikacji. Zdarzenia te są przetwarzane w wolnym SDM i środowiska IDE. Brak odpowiedzi są wysyłane do aparatu debugowania (DE), po przetworzeniu zdarzenia. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) i [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfejsy są przykłady zdarzeń asynchronicznych.  
  
- Zdarzenia synchroniczne  
  
   Powiadom SDM i środowisko IDE, który zmienia stan debugowanej aplikacji. Jedyną różnicą między te zdarzenia i asynchroniczne jest, że odpowiedź jest wysyłany przez [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metody.  
  
   Wysyłanie zdarzenia synchroniczne jest przydatne w przypadku usługi DE kontynuować przetwarzanie po IDE odbiera i przetwarza zdarzenia.  
  
- Synchroniczne zdarzeniami zatrzymującymi awarii lub zatrzymaniu albo zdarzenia  
  
   Powiadom SDM oraz środowiska IDE debugowanej aplikacji została zatrzymana, wykonywanie kodu. Podczas wysyłania zdarzeń Zatrzymywanie metodą [zdarzeń](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametr jest wymagany. Zatrzymywanie zdarzenia były obecne przez wywołanie jednej z następujących metod:  
  
  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) podano przykłady zatrzymywanie zdarzeń.  
  
  > [!NOTE]
  >  Zatrzymywanie asynchronicznego zdarzenia nie są obsługiwane. Jest to błąd, wysłać Zdarzenie asynchroniczne zatrzymywania.  
  
## <a name="discussion"></a>Dyskusja  
 Rzeczywiste wdrożenie zdarzeń zależy od projektu usługi DE. Typ każde zdarzenie przesłane jest określany przez jego atrybuty, które są ustawiane podczas projektowania DE. Na przykład może wysyłać jedną DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako zdarzenie asynchroniczne, podczas gdy inny może wysłać zdarzenie zatrzymywania.  
  
 W poniższej tabeli określono, które program i wątku parametry są wymagane dla których zdarzenia, a także typy zdarzeń. Dowolne zdarzenie, może być synchroniczne. Żadne zdarzenie musi być synchroniczne.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfejs jest wymagany dla wszystkich zdarzeń.  
  
|Zdarzenie|IDebugProgram2|IDebugThread2|Zatrzymywanie wydarzeń|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Wymagane|Wymagane|Nie|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Niedozwolone|Niedozwolone|Nie|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Niedozwolone|Niedozwolone|Nie|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Może być|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Może być|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Może być|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
|IDebugStopCompleteEvent2|Wymagane|Wymagane|Tak|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Wymagane|Wymagane|Nie|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Wymagane|Wymagane|Nie|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Może, ale nie jest wymagane|Może, ale nie jest wymagane|Nie|  
  
## <a name="see-also"></a>Zobacz także  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)