---
title: Breakpoint-Related metody | Microsoft Docs
description: Visual Studio debugowania obsługuje powiązane punkty przerwania, które zostały pomyślnie powiązane z lokalizacją w kodzie, oraz oczekujące punkty przerwania, które nie są jeszcze powiązane.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec218cea05dffc1c558cabdef47895da9ad7ba9c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901503"
---
# <a name="breakpoint-related-methods"></a>Metody związane z punktem przerwania
Aparat debugowania (DE) musi obsługiwać ustawienie punktów przerwania. Visual Studio debugowania obsługuje następujące typy punktów przerwania:

- Bound

     Żądane za pośrednictwem interfejsu użytkownika i pomyślnie powiązane z określoną lokalizacją kodu

- Oczekiwanie

     Żądane za pośrednictwem interfejsu użytkownika, ale jeszcze nie powiązane z rzeczywistymi instrukcjami

## <a name="discussion"></a>Dyskusja
 Na przykład oczekujący punkt przerwania występuje, gdy instrukcje nie są jeszcze załadowane. Po załadowaniu kodu oczekujące punkty przerwania próbują powiązać z kodem w zalecanej lokalizacji, czyli wstawić w kodzie instrukcje przerwania. Zdarzenia są wysyłane do menedżera debugowania sesji (SDM) w celu wskazania pomyślnego powiązania lub powiadomienia o błędach powiązań.

 Oczekujący punkt przerwania zarządza również własną wewnętrzną listą odpowiednich powiązanych punktów przerwania. Jeden oczekujący punkt przerwania może spowodować wstawienie wielu punktów przerwania w kodzie. Interfejs Visual Studio debugowania pokazuje widok drzewa oczekujących punktów przerwania i odpowiadających im powiązanych punktów przerwania.

 Tworzenie i używanie oczekujących punktów przerwania wymaga implementacji metody [IDebugEngine2::CreatePendingBreakpoint,](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) a także następujących metod interfejsów [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Metoda|Opis|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy określony oczekujący punkt przerwania może być powiązyny z lokalizacją kodu.|
|[Powiązać](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Wiąże określony oczekujący punkt przerwania z co najmniej jedną lokalizacją kodu.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan oczekującego punktu przerwania.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie punktu przerwania używane do tworzenia oczekującego punktu przerwania.|
|[Włączenie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Przełącza włączony stan oczekującego punktu przerwania.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania powiązane z oczekującym punktem przerwania.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów, które są wynikiem oczekującego punktu przerwania.|
|[Usuwanie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa oczekujący punkt przerwania i wszystkie powiązane z nim punkty przerwania.|

 Aby wyliczyć powiązane punkty przerwania i punkty przerwania błędów, należy zaimplementować wszystkie metody [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) i [IEnumDebugErrorBreakpoints2.](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)

 Oczekujące punkty przerwania, które są wiązane z lokalizacją kodu, wymagają implementacji następujących [metod IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania, który zawiera punkt przerwania.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan powiązanego punktu przerwania.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozwiązanie punktu przerwania opisujące punkt przerwania.|
|[Włączenie](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punkt przerwania.|
|[Usuwanie](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa powiązany punkt przerwania.|

 Informacje o rozwiązaniu i żądaniu wymagają implementacji następujących [metod IDebugBreakpointResolution2.](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania reprezentowanego przez rozwiązanie.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozwiązywaniu punktu przerwania, który opisuje punkt przerwania.|

 Rozwiązanie błędów, które mogą wystąpić podczas wiązania, wymaga implementacji następujących metod [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania, który zawiera punkt przerwania błędu.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Pobiera rozwiązanie błędu punktu przerwania opisujące punkt przerwania błędu.|

 Rozwiązanie błędów, które mogą wystąpić podczas wiązania, wymaga również następujących metod [rozwiązania IDebugErrorBreakpointResolution2.](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)

|Metoda|Opis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozwiązywaniu punktu przerwania.|

 Wyświetlanie kodu źródłowego w punkcie przerwania wymaga zaimplementowania metod [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i/lub metod [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
