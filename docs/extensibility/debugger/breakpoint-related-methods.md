---
title: Metody Breakpoint-Related | Microsoft Docs
description: Debugowanie programu Visual Studio obsługuje powiązane punkty przerwania, które zostały pomyślnie powiązane z lokalizacją w kodzie i oczekujące punkty przerwania, które nie są jeszcze powiązane.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c20a92e847f120850d7cbd424cc073018903911d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930827"
---
# <a name="breakpoint-related-methods"></a>Metody związane z punktem przerwania
Aparat debugowania (DE) musi obsługiwać ustawienie punktów przerwania. Debugowanie programu Visual Studio obsługuje następujące typy punktów przerwania:

- Bound

     Zażądano za pomocą interfejsu użytkownika i zostało pomyślnie powiązane z określoną lokalizacją w kodzie

- Oczekiwanie

     Zażądano za pomocą interfejsu użytkownika, ale jeszcze nie powiązano z rzeczywistymi instrukcjami

## <a name="discussion"></a>Dyskusja
 Na przykład oczekujący punkt przerwania występuje, gdy instrukcje nie są jeszcze załadowane. Gdy kod jest ładowany, oczekujące punkty przerwania próbują powiązać z kodem w określonej lokalizacji, czyli, aby wstawić instrukcje Break w kodzie. Zdarzenia są wysyłane do Menedżera debugowania sesji (SDM) w celu wskazania pomyślnego powiązania lub powiadomienia o błędach powiązania.

 Oczekujący punkt przerwania zarządza również własną wewnętrzną listę odpowiednich powiązanych punktów przerwania. Jeden oczekujący punkt przerwania może spowodować wstawienie wielu punktów przerwania w kodzie. Interfejs użytkownika debugowania programu Visual Studio pokazuje widok drzewa oczekujących punktów przerwania i odpowiadające im powiązane punkty przerwania.

 Tworzenie i używanie oczekujących punktów przerwania wymagają implementacji metody [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) , a także następujących metod interfejsów [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

|Metoda|Opis|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy określony oczekujący punkt przerwania można powiązać z lokalizacją w kodzie.|
|[Węglowodor](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Wiąże określony oczekujący punkt przerwania z co najmniej jedną lokalizacją kodu.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan oczekującego punktu przerwania.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie punktu przerwania użyte do utworzenia oczekującego punktu przerwania.|
|[Włączenie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Przełącza włączony stan oczekującego punktu przerwania.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania powiązane z oczekującego punktu przerwania.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów wynikające z oczekującego punktu przerwania.|
|[Usuwanie](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa oczekujący punkt przerwania i wszystkie punkty przerwania powiązane z nim.|

 Aby wyliczyć powiązane punkty przerwania i punkty przerwania błędów, należy zaimplementować wszystkie metody [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) i [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Oczekujące punkty przerwania, które wiążą się z lokalizacją w kodzie, wymagają implementacji następujących metod [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania, który zawiera punkt przerwania.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan powiązanego punktu przerwania.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozdzielczość punktu przerwania opisującą punkt przerwania.|
|[Włączenie](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punkt przerwania.|
|[Usuwanie](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa powiązany punkt przerwania.|

 Informacje o rozwiązywaniu i żądaniu wymagają implementacji następujących metod [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .

|Metoda|Opis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania reprezentowanego przez rozwiązanie.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punktu przerwania, które opisują punkt przerwania.|

 Rozwiązanie błędów, które mogą wystąpić podczas wiązania, wymaga implementacji następujących metod [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania, który zawiera błąd punktu przerwania.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Pobiera rozdzielczość błędu punktu przerwania opisującą punkt przerwania błędu.|

 Rozwiązanie błędów, które mogą wystąpić podczas tworzenia powiązania, wymaga również następujących metod [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Metoda|Opis|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punktu przerwania.|

 Wyświetlanie kodu źródłowego w punkcie przerwania wymaga wdrożenia metod [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i/lub metod [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania i Ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
