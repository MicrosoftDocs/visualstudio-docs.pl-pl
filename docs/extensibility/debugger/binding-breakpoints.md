---
title: Powiązywanie punktów przerwania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e839b6e0e7967c4802bee5617da3334c5d4033c5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903236"
---
# <a name="bind-breakpoints"></a>Powiązywanie punktów przerwania
Jeśli użytkownik ustawi punkt przerwania, na przykład przez naciśnięcie klawisza **F9**, IDE formułuje żądanie i poprosi o sesję debugowania, aby utworzyć punkt przerwania.

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania
 Ustawianie punktu przerwania jest procesem dwuetapowym, ponieważ kod lub dane, których dotyczy punkt przerwania, mogą nie być jeszcze dostępne. Najpierw należy opisać punkt przerwania, a następnie, ponieważ kod lub dane staną się dostępne, muszą być powiązane z tym kodem lub danymi w następujący sposób:

1. Punkt przerwania jest żądany z odpowiednich aparatów debugowania (DEs), a następnie punkt przerwania jest powiązany z kodem lub danymi, gdy staną się dostępne.

2. Żądanie punktu przerwania jest wysyłane do sesji debugowania, która wysyła je do wszystkich odpowiednich DEs. Wszystkie elementy, które wybierają, aby obsłużyć punkt przerwania tworzy odpowiadający mu oczekujący punkt przerwania.

3. Sesja debugowania zbiera oczekujące punkty przerwania i wysyła je z powrotem do pakietu debugowania (składnika debugowania programu Visual Studio).

4. Pakiet debugowania poprosi o sesję debugowania, aby powiązać oczekujący punkt przerwania z kodem lub danymi. Sesja debugowania wysyła to żądanie do wszystkich odpowiednich DEs.

5. Jeśli DE jest w stanie powiązać punkt przerwania, wysyła zdarzenie związane z punktem przerwania z powrotem do sesji debugowania. W przeciwnym razie zamiast tego wysyła zdarzenie błędu punktu przerwania.

## <a name="pending-breakpoints"></a>Oczekujące punkty przerwania
 Oczekujący punkt przerwania można powiązać z wieloma lokalizacjami kodu. Na przykład linia kodu źródłowego dla szablonu języka C++ może być powiązana z każdą sekwencją kodu wygenerowaną na podstawie szablonu. Sesja debugowania może użyć zdarzenia powiązanego z punktem przerwania, aby wyliczyć konteksty kodu powiązane z punktem przerwania w momencie wysłania zdarzenia. Więcej kontekstów kodu można powiązać w późniejszym czasie, więc wszystkie zdarzenia powiązane z elementem przerwania mogą być wysyłane dla każdego żądania bind. Jednakże element DE powinien wysyłać tylko jedno zdarzenie błędu punktu przerwania na żądanie powiązania.

## <a name="implementation"></a>Implementacja
 Programowo pakiet debugowania wywołuje Menedżera debugowania sesji (SDM) i udostępnia interfejs [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , który otacza strukturę [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) , która opisuje punkt przerwania, który ma zostać ustawiony. Mimo że punkty przerwania mogą być wieloma formularzami, ostatecznie są rozpoznawane jako kod lub kontekst danych.

 Model SDM przekazuje to wywołanie do każdego istotnego, wywołując metodę [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) . Jeśli element DE wybierze obsługę punktu przerwania, tworzy i zwraca interfejs [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) . Model SDM zbiera te interfejsy i przekazuje je z powrotem do pakietu debugowania jako jednego `IDebugPendingBreakpoint2` interfejsu.

 Do tej pory nie Wygenerowano żadnych zdarzeń.

 Pakiet debugowania próbuje powiązać oczekujący punkt przerwania do kodu lub danych przez wywołanie [powiązania](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), które jest implementowane przez de.

 Jeśli punkt przerwania jest powiązany, element DE wysyła interfejs zdarzenia [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) do pakietu debugowania. Pakiet debugowania używa tego interfejsu, aby wyliczyć wszystkie konteksty kodu (lub pojedynczy kontekst danych) powiązane z punktem przerwania, wywołując [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), który zwraca co najmniej jeden interfejs [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) . Interfejs [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) zwraca interfejs [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) , a [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) zwraca [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Union zawierający kod lub kontekst danych.

 Jeśli DE nie jest w stanie powiązać punktu przerwania, wysyła on pojedynczy interfejs zdarzenia [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do pakietu debugowania. Pakiet debugowania Pobiera typ błędu (błąd lub ostrzeżenie) i komunikat informacyjny przez wywołanie [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), po którym następuje [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) i [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). To zwraca strukturę [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) , która zawiera typ błędu i komunikat.

 Jeśli program nie obsługuje punktu przerwania, ale nie może go powiązać, zwraca błąd typu `BPET_TYPE_ERROR` . Pakiet debugowania reaguje, wyświetlając okno dialogowe błędu, a IDE umieszcza Symbol wykrzyknika wewnątrz symbolu punktu przerwania z lewej strony wiersza kodu źródłowego.

 Jeśli program nie obsługuje elementu przerwania, nie można powiązać go, ale niektóre inne nie mogą go powiązać, zwracając ostrzeżenie. IDE reaguje, umieszczając symbol zapytania w symbolu punktu przerwania z lewej strony wiersza kodu źródłowego.

## <a name="see-also"></a>Zobacz też
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
