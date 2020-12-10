---
title: Obsługiwane typy zdarzeń | Microsoft Docs
description: Dowiedz się więcej na temat typów zdarzeń obsługiwanych przez funkcję debugowania programu Visual Studio, w tym zdarzeń asynchronicznych, zdarzeń synchronicznych i zdarzeń zatrzymywania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 215256cbbcff45dfa0b85a480f0900e6f8ddfa71
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996035"
---
# <a name="supported-event-types"></a>Obsługiwane typy zdarzeń
Debugowanie programu Visual Studio obsługuje obecnie następujące typy zdarzeń:

- Zdarzenia asynchroniczne

   Powiadom Menedżera debugowania sesji (SDM) i IDE, że zmieniany jest stan debugowanej aplikacji. Te zdarzenia są przetwarzane przy użyciu modelu SDM i środowiska IDE. Po przetworzeniu zdarzenia nie jest wysyłana odpowiedź do aparatu debugowania. Interfejsy [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) i [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) są przykładami zdarzeń asynchronicznych.

- Zdarzenia synchroniczne

   Powiadom model SDM i środowisko IDE, aby zmienić stan debugowanej aplikacji. Jedyną różnicą między tymi zdarzeniami a zdarzeniami asynchronicznymi jest wysyłanie odpowiedzi przy użyciu metody [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

   Wysyłanie zdarzenia synchronicznego jest przydatne, jeśli konieczne jest kontynuowanie przetwarzania po odebraniu i przetworzeniu zdarzenia przez środowisko IDE.

- Synchroniczne zdarzenia zatrzymywania lub zatrzymywanie zdarzeń

   Powiadom model SDM i IDE, że debugowana aplikacja zatrzymała wykonywanie kodu. W przypadku wysyłania zdarzenia zatrzymania przy użyciu [zdarzenia](../../extensibility/debugger/reference/idebugeventcallback2-event.md)metody, parametr [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) jest wymagany. Zdarzenia zatrzymywania są kontynuowane przez wywołanie jednej z następujących metod:

  - [Wykonaj polecenie](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Krok](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Kontynuuj](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) są przykładami zdarzeń zatrzymywania.

  > [!NOTE]
  > Asynchroniczne zdarzenia zatrzymywania nie są obsługiwane. Wystąpił błąd podczas wysyłania asynchronicznego zdarzenia zatrzymania.

## <a name="discussion"></a>Dyskusja
 Rzeczywista implementacja zdarzeń zależy od projektu DE. Typ każdego wysyłanego zdarzenia jest określany przez jego atrybuty, które są ustawiane podczas projektowania. Na przykład jeden DE może wysyłać [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako zdarzenie asynchroniczne, a inne mogą wysłać je jako zdarzenie zatrzymywania.

 W poniższej tabeli określono, które parametry programu i wątku są wymagane dla zdarzeń, a także typów zdarzeń. Każde zdarzenie może być synchroniczne. Żadne zdarzenie nie musi być synchroniczne.

> [!NOTE]
> Interfejs [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) jest wymagany dla wszystkich zdarzeń.

|Wydarzenie|IDebugProgram2|IDebugThread2|Zatrzymywanie zdarzeń|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Wymagane|Wymagane|Nie|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Niedozwolone|Niedozwolone|Nie|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Niedozwolone|Niedozwolone|Nie|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Może być|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Może być|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Może być|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Wymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Wymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Wymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Wymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Wymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|
|IDebugStopCompleteEvent2|Wymagane|Wymagane|Tak|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Wymagane|Wymagane|Tak|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Wymagane|Wymagane|Nie|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Wymagane|Wymagane|Nie|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Dozwolone, ale niewymagane|Dozwolone, ale niewymagane|Nie|

## <a name="see-also"></a>Zobacz też
- [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)
