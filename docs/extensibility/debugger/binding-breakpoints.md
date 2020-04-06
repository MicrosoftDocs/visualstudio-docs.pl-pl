---
title: Punkty przerwania wiązania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739231"
---
# <a name="bind-breakpoints"></a>Punkty przerwania wiązania
Jeśli użytkownik ustawi punkt przerwania, być może naciskając **klawisz F9,** IDE formułuje żądanie i monituje sesję debugowania, aby utworzyć punkt przerwania.

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania
 Ustawienie punktu przerwania jest procesem dwuetapowym, ponieważ kod lub dane, których dotyczy punkt przerwania, mogą nie być jeszcze dostępne. Najpierw punkt przerwania musi być opisany, a następnie, gdy kod lub dane stają się dostępne, musi być powiązany z tym kodem lub danymi w następujący sposób:

1. Punkt przerwania jest wymagane z odpowiednich aparatów debugowania (DEs), a następnie punkt przerwania jest powiązany z kodem lub danymi, gdy staną się dostępne.

2. Żądanie punktu przerwania jest wysyłane do sesji debugowania, która wysyła go do wszystkich odpowiednich DEs. Każdy DE, który zdecyduje się obsłużyć punkt przerwania tworzy odpowiedni oczekujący punkt przerwania.

3. Sesja debugowania zbiera oczekujące punkty przerwania i wysyła je z powrotem do pakietu debugowania (składnik debugowania programu Visual Studio).

4. Pakiet debugowania monituje sesji debugowania do powiązania oczekującego punktu przerwania do kodu lub danych. Sesja debugowania wysyła to żądanie do wszystkich odpowiednich DEs.

5. Jeśli DE jest w stanie powiązać punkt przerwania, wysyła zdarzenie związane z punktem przerwania z powrotem do sesji debugowania. Jeśli nie, wysyła zdarzenie błędu punktu przerwania zamiast tego.

## <a name="pending-breakpoints"></a>Oczekujące punkty przerwania
 Oczekujący punkt przerwania może powiązać z wieloma lokalizacjami kodu. Na przykład wiersz kodu źródłowego dla szablonu Języka C++ można powiązać z każdej sekwencji kodu generowane z szablonu. Sesja debugowania można użyć zdarzenia powiązanego z punktem przerwania do wyliczenia kontekstów kodu powiązanych z punktem przerwania w momencie wysłania zdarzenia. Więcej kontekstów kodu mogą być powiązane później, więc DE może wysyłać wiele zdarzeń związanych punktu przerwania dla każdego żądania powiązania. Jednak DE należy wysłać tylko jedno zdarzenie błędu punktu przerwania na żądanie powiązania.

## <a name="implementation"></a>Wdrażanie
 Programowo pakiet debugowania wywołuje menedżera debugowania sesji (SDM) i nadaje mu interfejs [IDebugBreakpointRequest2,](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) który zawija strukturę [BP_REQUEST_INFO,](../../extensibility/debugger/reference/bp-request-info.md) która opisuje punkt przerwania, który ma zostać ustawiony. Mimo że punkty przerwania mogą być z wielu formularzy, ostatecznie rozwiązać do kontekstu kodu lub danych.

 SDM przekazuje to wywołanie do każdego odpowiedniego DE, wywołując jego [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metody. Jeśli DE zdecyduje się obsłużyć punkt przerwania, tworzy i zwraca interfejs [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Moduł SDM zbiera te interfejsy i przekazuje je z `IDebugPendingBreakpoint2` powrotem do pakietu debugowania jako pojedynczy interfejs.

 Do tej pory nie wygenerowano żadnych zdarzeń.

 Pakiet debugowania następnie próbuje powiązać oczekujący punkt przerwania z kodem lub danymi, wywołując [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), który jest implementowany przez DE.

 Jeśli punkt przerwania jest powiązany, DE wysyła interfejs zdarzenia [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) do pakietu debugowania. Pakiet debugowania używa tego interfejsu do wyliczenia wszystkich kontekstów kodu (lub kontekstu pojedynczego danych) powiązanego z punktem przerwania przez wywołanie [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), który zwraca jeden lub więcej interfejsów [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Interfejs [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) zwraca interfejs [IDebugBreakpointResolution2,](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) a [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) zwraca [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) unii zawierającej kontekst kodu lub danych.

 Jeśli DE nie jest w stanie powiązać punkt przerwania, wysyła jeden interfejs zdarzenia [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do pakietu debugowania. Pakiet debugowania pobiera typ błędu (błąd lub ostrzeżenie) i komunikat informacyjny, wywołując [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), a następnie [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) i [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Zwraca [strukturę BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) zawierającą typ błędu i komunikat.

 Jeśli DE obsługuje punkt przerwania, ale nie może go `BPET_TYPE_ERROR`powiązać, zwraca błąd typu . Pakiet debugowania odpowiada, wyświetlając okno dialogowe błędu, a IDE umieszcza glif wykrzyknika wewnątrz glifu punktu przerwania po lewej stronie wiersza kodu źródłowego.

 Jeśli DE obsługuje punkt przerwania, nie można powiązać go, ale niektóre inne DE może powiązać go, zwraca ostrzeżenie. IDE odpowiada, umieszczając glif pytanie wewnątrz glifu punktu przerwania po lewej stronie wiersza kodu źródłowego.

## <a name="see-also"></a>Zobacz też
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
