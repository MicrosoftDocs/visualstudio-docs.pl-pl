---
title: Metody dotyczące punktu przerwania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f7904a1ae38ce9a2c8103208490bc67e8dc7b1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799185"
---
# <a name="breakpoint-related-methods"></a>Metody dotyczące punktu przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aparat debugowania (DE) musi obsługiwać ustawienie punktów przerwania. Debugowanie programu Visual Studio obsługuje następujące typy punktów przerwania:  
  
-   powiązane  
  
     Żądanie za pośrednictwem interfejsu użytkownika i pomyślnie powiązane z lokalizacją określony kod  
  
-   Oczekujące  
  
     Żądanie za pośrednictwem interfejsu użytkownika, ale jeszcze nie jest powiązana z rzeczywistych instrukcje  
  
## <a name="discussion"></a>Dyskusja  
 Na przykład oczekujący punkt przerwania występuje, gdy instrukcje nie zostały jeszcze załadowane. Gdy kod jest ładowany, oczekujących spróbuj punktów przerwania można powiązać kod w określonej lokalizacji, oznacza to, aby wstawić podział instrukcji w kodzie. Zdarzenia są wysyłane do Menedżer debugowania sesji (SDM) wskazuje pomyślne powiązania lub powiadomienie, że wystąpiły błędy powiązania.  
  
 Oczekujący punkt przerwania zarządza także swój własny wewnętrzną listę odpowiednich powiązanych punktów przerwania. Jeden oczekujący punkt przerwania może spowodować wstawiania wielu punktów przerwania w kodzie. Debugowania interfejsu użytkownika programu Visual Studio Pokazuje widok drzewa oczekujących punktów przerwania i odpowiadające im powiązane punkty przerwania.  
  
 Stworzeniem i używaniem oczekujących punktów przerwania wymagają wykonania [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metody, jak również z następujących metod [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy określony oczekujących punktów przerwania można powiązać z lokalizacji kodu.|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Wiąże określoną oczekujących punktów przerwania z jedną lub więcej lokalizacji kodu.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan oczekujący punkt przerwania.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie przerwania, użyty do utworzenia oczekujący punkt przerwania.|  
|[Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Włącza/wyłącza włączony stan oczekujący punkt przerwania.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania, powiązana z oczekującym punktem przerwania.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów wynikających z Oczekujący punkt przerwania.|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa oczekujący punkt przerwania i wszystkie punkty przerwania, powiązany z niego.|  
  
 Wyliczyć powiązane punkty przerwania i punkty przerwania błędu musi implementować wszystkie metody [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) i [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Oczekujące punkty przerwania, które należy powiązać kod lokalizacji wymaga wykonania następujących [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania, który zawiera punkt przerwania.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan powiązany punkt przerwania.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozwiązanie punktu przerwania, który opisuje punktu przerwania.|  
|[Enable](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punkt przerwania.|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa powiązany punkt przerwania.|  
  
 Rozdzielczość i żądanie informacji wymaga wykonania następujących [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania reprezentowany przez rozwiązania.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punkt przerwania, opisujący punktu przerwania.|  
  
 Rozpoznawanie błędów, które mogą wystąpić podczas tworzenia powiązania wymaga wykonania następujących [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania, który zawiera błąd punktu przerwania.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Pobiera rozwiązanie błąd punktu przerwania, który opisuje błąd punktu przerwania.|  
  
 Rozpoznawanie błędów, które mogą wystąpić podczas tworzenia powiązania wymaga również z następujących metod [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozwiązania punktu przerwania.|  
  
 Wyświetlanie kodu źródłowego w punkcie przerwania, musisz zaimplementować metody [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i/lub metody [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
