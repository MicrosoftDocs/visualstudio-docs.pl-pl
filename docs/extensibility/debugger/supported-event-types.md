---
title: Obsługiwane typy zdarzeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712802"
---
# <a name="supported-event-types"></a>Obsługiwane typy zdarzeń
Debugowanie programu Visual Studio obsługuje obecnie następujące typy zdarzeń:

- Zdarzenia asynchroniczne

   Powiadom menedżera debugowania sesji (SDM) i IDE, że zmienia się stan debugowana aplikacji. Zdarzenia te są przetwarzane w czasie wolnym od SDM i IDE. Żadna odpowiedź nie jest wysyłana do aparatu debugowania (DE) po przetworzeniu zdarzenia. Interfejsy [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) i [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) są przykładami zdarzeń asynchronicznych.

- Zdarzenia synchroniczne

   Powiadom SDM i IDE, że zmienia się stan aplikacji debugowane. Jedyną różnicą między tymi zdarzeniami i zdarzeniami asynchronizatycznymi jest to, że odpowiedź jest wysyłana za pomocą [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metody.

   Wysyłanie zdarzenia synchronicznego jest przydatne, jeśli potrzebujesz de, aby kontynuować przetwarzanie po odbierze IDE i przetwarza zdarzenie.

- Zdarzenia zatrzymania synchronicznego lub zatrzymania zdarzeń

   Powiadom SDM i IDE, że aplikacja jest debugowana przestała wykonywać kod. Podczas wysyłania zdarzenia zatrzymania za pomocą metody [Zdarzenia](../../extensibility/debugger/reference/idebugeventcallback2-event.md)wymagany jest parametr [IDebugThread2.](../../extensibility/debugger/reference/idebugthread2.md) Zatrzymywanie zdarzeń są kontynuowane przez wywołanie jednej z następujących metod:

  - [Realizacja](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Krok](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Kontynuować](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) są przykładami zatrzymywania zdarzeń.

  > [!NOTE]
  > Zdarzenia zatrzymania asynchronii nie są obsługiwane. Jest to błąd, aby wysłać zdarzenie zatrzymania asynchronii.

## <a name="discussion"></a>Dyskusji
 Rzeczywista realizacja zdarzeń zależy od projektu de. Typ każdego zdarzenia wysyłane zależy od jego atrybutów, które są ustawiane podczas projektowania DE. Na przykład jeden DE może wysłać [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako zdarzenie asynchroniczne, podczas gdy inny może wysłać go jako zdarzenie zatrzymania.

 W poniższej tabeli określono, które parametry programu i wątku są wymagane dla których zdarzeń, a także typy zdarzeń. Każde zdarzenie może być synchroniczne. Żadne zdarzenie nie musi być synchroniczne.

> [!NOTE]
> Interfejs [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) jest wymagany dla wszystkich zdarzeń.

|Wydarzenie|IDebugProgram2|IDebugThread2|Zatrzymywanie zdarzeń|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Wymagany|Wymagany|Tak|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Wymagany|Wymagany|Tak|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Wymagany|Wymagany|Nie|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Niedozwolone|Niedozwolone|Nie|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Niedozwolone|Niedozwolone|Nie|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Wymagany|Wymagany|Tak|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Można|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Wymagany|Wymagany|Tak|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Można|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Wymagany|Wymagany|Tak|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Wymagany|Wymagany|Tak|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Można|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Wymagany|Dozwolone, ale nie wymagane|Nie|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Wymagany|Dozwolone, ale nie wymagane|Nie|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Wymagany|Dozwolone, ale nie wymagane|Nie|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Wymagany|Dozwolone, ale nie wymagane|Nie|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Wymagany|Dozwolone, ale nie wymagane|Nie|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|IDebugStopCompleteEvent2|Wymagany|Wymagany|Tak|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Wymagany|Wymagany|Tak|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Wymagany|Wymagany|Nie|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Wymagany|Wymagany|Nie|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Dozwolone, ale nie wymagane|Dozwolone, ale nie wymagane|Nie|

## <a name="see-also"></a>Zobacz też
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
