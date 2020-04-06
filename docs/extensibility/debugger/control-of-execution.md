---
title: Kontrola wykonania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739076"
---
# <a name="control-of-execution"></a>Kontrola wykonania
Aparat debugowania (DE) zazwyczaj wysyła jedno z następujących zdarzeń jako ostatnie zdarzenie uruchamiania:

- Zdarzenie punktu wejścia, jeśli dołączanie do nowo uruchomionego programu

- Zdarzenie zakończenie ładowania, jeśli dołączanie do programu, który jest już uruchomiony

  Oba te zdarzenia są zatrzymywanie zdarzeń, co oznacza, że DE czeka na odpowiedź od użytkownika za pomocą IDE. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Zdarzenie zatrzymania
 Gdy zdarzenie zatrzymania jest wysyłane do sesji debugowania:

1. Program i wątek, które zawierają bieżący wskaźnik instrukcji można uzyskać z interfejsu zdarzenia.

2. IDE określa bieżący plik kodu źródłowego i pozycję, który jest wyświetlany jako wyróżniony w edytorze.

3. Sesja debugowania zazwyczaj odpowiada na to pierwsze zdarzenie zatrzymania, wywołując metodę **Continue** programu.

4. Program jest następnie uruchamiany, dopóki nie napotka stanu zatrzymania, takiego jak trafienie punktu przerwania. W takim przypadku DE wysyła zdarzenie punktu przerwania do sesji debugowania. Zdarzenie punktu przerwania jest zdarzeniem zatrzymania i DE ponownie czeka na odpowiedź użytkownika.

5. Jeśli użytkownik zdecyduje się wkroczyć, nad lub z funkcji, IDE monituje sesji debugowania `Step` do wywołania metody programu. IDE następnie przekazuje jednostkę kroku (instrukcja, instrukcja lub wiersz) i typ kroku (czy krok do, nad lub z funkcji). Po zakończeniu kroku DE wysyła zdarzenie ukończenia kroku do sesji debugowania, która jest zdarzeniem zatrzymania.

    — lub —

    Jeśli użytkownik zdecyduje się kontynuować wykonywanie z bieżącego wskaźnika instrukcji, IDE monituje sesji debugowania do wywołania programu **Execute** metody. Program wznawia wykonywanie, dopóki nie napotka następnego stanu zatrzymania.

    — lub —

    Jeśli sesja debugowania ma zignorować określone zdarzenie zatrzymania, sesja debugowania wywołuje metodę **Continue** programu. Jeśli program był stepping into, over, lub out of a function when it encountered the stopping condition, then it continues the step.

   Programowo, gdy DE napotka warunek zatrzymania, wysyła takie zdarzenia zatrzymania jak [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do menedżera debugowania sesji (SDM) za pomocą interfejsu [IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) DE przekazuje [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) i [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfejsów, które reprezentują program i wątek zawierający bieżący wskaźnik instrukcji. SDM wywołuje [IDebugThread2::EnumFrameInfo,](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) aby uzyskać górną ramkę stosu i wywołuje [IDebugStackFrame2::GetDocumentContext,](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) aby uzyskać kontekst dokumentu skojarzony z bieżącym wskaźnikiem instrukcji. Ten kontekst dokumentu jest zazwyczaj nazwą pliku kodu źródłowego, wierszem i numerem kolumny. IDE używa ich do podświetlenia kodu źródłowego, który zawiera bieżący wskaźnik instrukcji.

   SDM zazwyczaj odpowiada na to pierwsze zdarzenie zatrzymania, wywołując [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Program następnie uruchamia się, dopóki nie napotka warunek zatrzymania, takich jak uderzenie punktu przerwania, w którym to przypadku DE wysyła [IDebugBreakpointEvent2 interface](../../extensibility/debugger/reference/idebugbreakpointevent2.md) do SDM. Zdarzenie punktu przerwania jest zdarzeniem zatrzymania i DE ponownie czeka na odpowiedź użytkownika.

   Jeśli użytkownik zdecyduje się wkroczyć, nad lub z funkcji, IDE monituje SDM do wywołania [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). IDE następnie przekazuje [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrukcja, instrukcja lub wiersz) i [STEPKIND](../../extensibility/debugger/reference/stepkind.md), czyli, czy krok do, ponad lub z funkcji. Po zakończeniu kroku DE wysyła interfejs [IDebugStepLeteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) do SDM, który jest zdarzeniem zatrzymania.

   Jeśli użytkownik zdecyduje się kontynuować wykonywanie z bieżącego wskaźnika instrukcji, IDE prosi SDM do wywołania [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Program wznawia wykonywanie, dopóki nie napotka następnego stanu zatrzymania.

   Jeśli pakiet debugowania ma zignorować określone zdarzenie zatrzymania, pakiet debugowania wywołuje SDM, który wywołuje [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Jeśli program był stepping into, over, lub out of a function when it encountered the stopping condition, it continues the step. Oznacza to, że program utrzymuje stan stepping, tak, że wie, jak kontynuować.

   Wywołania SDM do `Step`, **Execute**i **Continue** są asynchroniczne, co oznacza, że SDM oczekuje, że wywołanie szybko powrócić. Jeśli DE wysyła SDM zdarzenie zatrzymania w `Step`tym samym wątku przed , **Execute**lub **Continue** zwraca, SDM zawiesza.

## <a name="see-also"></a>Zobacz też
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
