---
title: Kontrola wykonywania | Microsoft Docs
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
ms.openlocfilehash: 9c59831efb2fc97ad1bb2891fd93a67fe79f8eff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387008"
---
# <a name="control-of-execution"></a>Kontrola wykonywania
Aparat debugowania (DE) zwykle wysyła jedno z następujących zdarzeń jako ostatnie zdarzenie uruchamiania:

- Zdarzenie punktu wejścia w przypadku dołączania do nowo uruchomionego programu

- Zdarzenie ukończenia ładowania, jeśli dołączanie do programu, który jest już uruchomiony

  Oba te zdarzenia są zatrzymywane zdarzenia, co oznacza, że czas oczekiwania na odpowiedź od użytkownika jest spowodowany przez środowisko IDE. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Zatrzymywanie zdarzenia
 Po wysłaniu zdarzenia zatrzymania do sesji debugowania:

1. Program i wątek, który zawiera bieżący wskaźnik instrukcji, można uzyskać z interfejsu zdarzenia.

2. IDE określa bieżący plik i położenie kodu źródłowego, który jest wyświetlany jako wyróżniony w edytorze.

3. Sesja debugowania zazwyczaj odpowiada na to pierwsze zdarzenie zatrzymywania przez wywołanie metody **Kontynuuj** programu.

4. Program zostanie uruchomiony do momentu napotkania warunku zatrzymania, takiego jak naciśnięcie punktu przerwania. W takim przypadku element DE wysyła zdarzenie punktu przerwania do sesji debugowania. Zdarzenie punktu przerwania jest zdarzeniem zatrzymania, a czas oczekiwania na odpowiedź użytkownika.

5. Jeśli użytkownik wybierze krok po kroku, przekroczenia lub z funkcji, IDE będzie monitował sesję debugowania, aby wywołać `Step` metodę programu. Środowisko IDE przekazuje następnie jednostkę kroku (instrukcję, instrukcję lub line) i typ kroku (określa, czy należy wkroczyć, przekroczyć lub z funkcji). Po wykonaniu kroku element DE wysyła zdarzenie Ukończ krok do sesji debugowania, która jest zdarzeniem zatrzymania.

    -lub-

    Jeśli użytkownik zdecyduje się kontynuować wykonywanie od bieżącego wskaźnika instrukcji, IDE poprosi o sesję debugowania, aby wywołać metodę **Execute** programu. Program wznawia wykonywanie do momentu napotkania następnego warunku zatrzymywania.

    -lub-

    Jeśli sesja debugowania to ignorowanie określonego zdarzenia zatrzymania, sesja debugowania wywołuje metodę **Continue** programu. Jeśli program przeprowadził do, przekroczenia lub z funkcji po napotkaniu warunku zatrzymania, kontynuuje ten krok.

   Program programowo, gdy napotyka warunek zatrzymania, wysyła takie zdarzenia zatrzymywania jako [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do Menedżera debugowania sesji (SDM) za pomocą interfejsu [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . Powoduje, że interfejsy [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) i [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) reprezentujące program i wątek zawierający bieżący wskaźnik instrukcji. Model SDM wywołuje [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) , aby pobrać górną ramkę stosu i wywołuje [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) w celu pobrania kontekstu dokumentu skojarzonego z bieżącym wskaźnikiem instrukcji. Ten kontekst dokumentu jest zazwyczaj nazwą pliku kodu źródłowego, wierszem i numerem kolumny. IDE używa tych funkcji do wyróżnienia kodu źródłowego, który zawiera bieżący wskaźnik instrukcji.

   Model SDM zazwyczaj odpowiada na to pierwsze zdarzenie zatrzymywania przez wywołanie [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Program zostanie uruchomiony do momentu napotkania warunku zatrzymania, takiego jak naciśnięcie punktu przerwania, w którym to przypadku DE wysyła [interfejs IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) do modelu SDM. Zdarzenie punktu przerwania jest zdarzeniem zatrzymania, a czas oczekiwania na odpowiedź użytkownika.

   Jeśli użytkownik zdecyduje się na przekroczenie lub wyjście z funkcji, IDE poprosi model SDM o wywołanie [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md). IDE przekazuje następnie [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrukcję, instrukcję lub line) i [STEPKIND](../../extensibility/debugger/reference/stepkind.md), czyli czy należy wkroczyć, przekroczyć lub z funkcji. Po zakończeniu kroku element DE wysyła Interfejs [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) do modelu SDM, który jest zdarzeniem zatrzymywania.

   Jeśli użytkownik zdecyduje się kontynuować wykonywanie od bieżącego wskaźnika instrukcji, IDE prosi model SDM o wywołanie [IDebugProgram2:: Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Program wznawia wykonywanie do momentu napotkania następnego warunku zatrzymywania.

   Jeśli pakietem debugowania jest ignorowanie określonego zdarzenia zatrzymania, pakiet debugowania wywołuje model SDM, który wywołuje [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Jeśli program przeprowadził do, przekroczenia lub z funkcji po napotkaniu warunku zatrzymania, kontynuuje ten krok. Oznacza to, że program zachowuje stan stopniowania, dzięki czemu wie, jak kontynuować.

   Wywołania modelu SDM `Step` są **wykonywane**, a i **kontynuuje** są asynchroniczne, co oznacza, że model SDM oczekuje, że wywołanie ma być szybko zwracane. Jeśli po stronie Anuluj wyśle zdarzenie zatrzymywania modelu SDM w tym samym wątku przed `Step` , **Execute**lub **Continue** , model SDM przestanie odpowiadać.

## <a name="see-also"></a>Zobacz też
- [Debuguj zadania](../../extensibility/debugger/debugging-tasks.md)
