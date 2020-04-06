---
title: Metody związane z punktami przerwania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739212"
---
# <a name="breakpoint-related-methods"></a>Metody związane z punktem przerwania
Aparat debugowania (DE) musi obsługiwać ustawienie punktów przerwania. Debugowanie programu Visual Studio obsługuje następujące typy punktów przerwania:

- Bound

     Żądana za pośrednictwem interfejsu użytkownika i pomyślnie powiązana z określoną lokalizacją kodu

- Oczekujące

     Wymagane za pośrednictwem interfejsu użytkownika, ale jeszcze nie związane z rzeczywistymi instrukcjami

## <a name="discussion"></a>Dyskusji
 Na przykład oczekujący punkt przerwania występuje, gdy instrukcje nie są jeszcze załadowane. Po załadowaniu kodu oczekujące punkty przerwania próbują powiązać z kodem w określonej lokalizacji, czyli wstawić instrukcje przerwania w kodzie. Zdarzenia są wysyłane do menedżera debugowania sesji (SDM), aby wskazać pomyślne powiązanie lub powiadomić, że wystąpiły błędy wiązania.

 Oczekujący punkt przerwania zarządza również własną wewnętrzną listę odpowiednich powiązanych punktów przerwania. Jeden oczekujący punkt przerwania może spowodować wstawienie wielu punktów przerwania w kodzie. Interfejs użytkownika debugowania programu Visual Studio pokazuje widok drzewa oczekujących punktów przerwania i ich odpowiednich punktów przerwania.

 Tworzenie i używanie oczekujących punktów przerwania wymaga implementacji [metody IDebugEngine2::CreatePendingBreakpoint,](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) a także następujących metod interfejsów [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Metoda|Opis|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy określony oczekujący punkt przerwania może powiązać z lokalizacją kodu.|
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Wiąże określony oczekujący punkt przerwania z co najmniej jedną lokalizacją kodu.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan oczekującego punktu przerwania.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie punktu przerwania używane do tworzenia oczekującego punktu przerwania.|
|[Włącz](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Przełącza włączony stan oczekującego punktu przerwania.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania powiązane z oczekującym punktem przerwania.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów, które wynikają z oczekującego punktu przerwania.|
|[Usuwanie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa oczekujący punkt przerwania i wszystkie punkty przerwania powiązane z nim.|

 Aby wyliczyć powiązane punkty przerwania i punkty przerwania błędów, należy zaimplementować wszystkie metody [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) i [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Oczekujące punkty przerwania, które wiążą się z lokalizacją kodu wymagają implementacji następujących metod [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujących punkt przerwania, który zawiera punkt przerwania.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan powiązanego punktu przerwania.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozdzielczość punktu przerwania, który opisuje punkt przerwania.|
|[Włącz](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punkt przerwania.|
|[Usuwanie](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa powiązany punkt przerwania.|

 Informacje o rozdzielczości i żądaniu wymagają implementacji następujących metod [IDebugBreakpointResolution2.](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania reprezentowane przez rozdzielczość.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punktu przerwania, który opisuje punkt przerwania.|

 Rozwiązywanie błędów, które mogą wystąpić podczas wiązania wymaga implementacji następujących [metod IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujących punkt przerwania, który zawiera punkt przerwania błędu.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Pobiera rozpoznawanie błędów punktu przerwania, który opisuje punkt przerwania błędu.|

 Rozwiązywanie błędów, które mogą wystąpić podczas wiązania wymaga również następujących metod [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Metoda|Opis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punktu przerwania.|

 Wyświetlanie kodu źródłowego w punkcie przerwania wymaga zaimplementowania metod [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i/lub metod [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
