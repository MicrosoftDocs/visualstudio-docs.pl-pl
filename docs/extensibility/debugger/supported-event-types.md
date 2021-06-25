---
title: Obsługiwane typy zdarzeń | Microsoft Docs
description: Dowiedz się więcej na temat typów zdarzeń Visual Studio, w tym zdarzeń asynchronicznych, zdarzeń synchronicznych i zdarzeń zatrzymywania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fff86a142f541c1b17012b6190dd68e8d5628a3c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902907"
---
# <a name="supported-event-types"></a>Obsługiwane typy zdarzeń
Visual Studio obecnie obsługuje następujące typy zdarzeń:

- Zdarzenia asynchroniczne

   Powiadom menedżera debugowania sesji (SDM) i środowiska IDE, że stan debugowanych aplikacji zmienia się. Te zdarzenia są przetwarzane w programie SDM i w idee. Po przetworzeniu zdarzenia do aparatu debugowania nie jest wysyłana żadna odpowiedź. Interfejsy [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) [i IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) są przykładami zdarzeń asynchronicznych.

- Zdarzenia synchroniczne

   Powiadom program SDM i ideę o zmianie stanu debugowanych aplikacji. Jedyną różnicą między tymi zdarzeniami i zdarzeniami asynchronicznym jest to, że odpowiedź jest wysyłana za pomocą metody [ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

   Wysyłanie zdarzenia synchronicznego jest przydatne, jeśli potrzebujesz DE kontynuować przetwarzanie po ide odbiera i przetwarza zdarzenie.

- Synchroniczne zatrzymywanie zdarzeń lub zatrzymywanie zdarzeń

   Powiadom program SDM i środowiska IDE, że debugowana aplikacja przestała wykonywanie kodu. W przypadku wysyłania zdarzenia zatrzymania za pomocą metody [Zdarzenie](../../extensibility/debugger/reference/idebugeventcallback2-event.md)wymagany jest parametr [IDebugThread2.](../../extensibility/debugger/reference/idebugthread2.md) Zatrzymywanie zdarzeń jest kontynuowane przez wywołanie jednej z następujących metod:

  - [Wykonaj polecenie](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Krok](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Kontynuuj](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) [i IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) są przykładami zatrzymywania zdarzeń.

  > [!NOTE]
  > Asynchroniczne zdarzenia zatrzymywania nie są obsługiwane. Wysyłanie asynchronicznego zdarzenia zatrzymywania jest błędem.

## <a name="discussion"></a>Dyskusja
 Rzeczywista implementacja zdarzeń zależy od projektu de. Typ każdego wysyłanego zdarzenia zależy od jego atrybutów, które są ustawiane podczas projektowania de. Na przykład jedno de może wysłać [zdarzenie IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako zdarzenie asynchroniczne, a inne może wysłać je jako zdarzenie zatrzymywania.

 W poniższej tabeli określono, które parametry programu i wątku są wymagane dla których zdarzeń, a także typów zdarzeń. Każde zdarzenie może być synchroniczne. Żadne zdarzenie nie musi być synchroniczne.

> [!NOTE]
> Interfejs [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) jest wymagany dla wszystkich zdarzeń.

|Zdarzenie|IDebugProgram2|IDebugThread2|Zatrzymywanie zdarzeń|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Wymagane|Wymagane|Nie|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Niedozwolone|Niedozwolone|Nie|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Niedozwolone|Niedozwolone|Nie|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Może być|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Może być|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Może być|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|IDebugStopCompleteEvent2|Wymagane|Wymagane|Tak|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Wymagane|Wymagane|Nie|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Wymagane|Wymagane|Nie|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|

## <a name="see-also"></a>Zobacz też
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
