---
title: Tworzenie powiązań punktów przerwania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b94960130ef0b384a7e3a946dcbd2a4e4794252f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795890"
---
# <a name="binding-breakpoints"></a>Tworzenie powiązań punktów przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jeśli użytkownik ustawia punkt przerwania, może być, naciskając klawisz F9, IDE formulates żądanie i wyświetla monit o sesji debugowania, aby utworzyć punkt przerwania.  
  
## <a name="setting-a-breakpoint"></a>Ustawienie punktu przerwania  
 Ustawienie punktu przerwania jest procesem dwuetapowym, ponieważ kod lub wpływ punkt przerwania danych mogą jeszcze być niedostępne. Najpierw należy opisać punkt przerwania, a następnie kodu lub danych staje się dostępny, jego musi być powiązana z tego kodu lub danych, w następujący sposób:  
  
1.  Punkt przerwania zostanie wywołana z silniki debugowania odpowiednie (DEs), a następnie punkt przerwania jest powiązany z kodu lub danych, po jej udostępnieniu.  
  
2.  Żądanie przerwania jest wysyłane do sesji debugowania i wysyła je do wszystkich odpowiednich DEs. Wszelkie DE, który wybiera do obsługi punktu przerwania tworzy odpowiedni oczekujących punktów przerwania.  
  
3.  Sesja debugowania umożliwia zbieranie informacji o oczekujących punktów przerwania i wysyła je do pakietu debugowania (składnik debugowania programu Visual Studio).  
  
4.  Debugowanie pakietu monituje o sesji debugowania, aby powiązać oczekujący punkt przerwania z kodu lub danych. Sesja debugowania wysyła to żądanie do wszystkich odpowiednich DEs.  
  
5.  Jeśli DE jest w stanie powiązać punkt przerwania, wysyła to, że punkt przerwania powiązane zdarzenia do sesji debugowania. W przeciwnym razie zamiast wysyła zdarzenie błąd punktu przerwania.  
  
## <a name="pending-breakpoints"></a>Oczekujących punktów przerwania  
 Oczekujący punkt przerwania można powiązać wiele lokalizacji kodu. Na przykład wiersz kodu źródłowego dla szablonów języka C++ można powiązać każdy sekwencji kod generowany na podstawie szablonu. Sesja debugowania zdarzenia można użyć w punkt przerwania powiązanej wyliczyć kontekstów kod powiązany punkt przerwania w czasie, w którym zdarzenie zostało wysłane. Więcej kontekstów kod może być powiązana później, więc DE może wysłać zdarzenia dla każdego żądania powiązania powiązany wiele punkt przerwania. Jednak DE należy wysłać tylko jedno zdarzenie błędu punkt przerwania na żądania powiązania.  
  
## <a name="implementation"></a>Implementacja  
 Programowo, debugowanie pakietu wywołuje debugowania sesji manager (SDM) i nadaje jej [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfejsu, który otacza [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) struktury, która opisuje punkt przerwania do ustawienia. Mimo że punkty przerwania może mieć wiele form, ostatecznie rozpoznają do kontekstu kodu lub danych.  
  
 SDM przekazuje tego wywołania do każdego odpowiedniego DE przez wywołanie jego [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metody. Jeśli wybierze DE do obsługi punktu przerwania, tworzy i zwraca [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfejsu. Model SDM umożliwia zbieranie informacji o tych interfejsów i przekazuje je do pakietu debugowania jako pojedynczy `IDebugPendingBreakpoint2` interfejsu.  
  
 Do tej pory zostały wygenerowane żadne zdarzenia.  
  
 Debugowanie pakietu podejmuje oczekujący punkt przerwania można powiązać kod lub dane, wywołując [powiązać](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), który jest implementowany przez DE.  
  
 Jeśli punkt przerwania jest związany, DE wysyła [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfejsu zdarzenia do pakietu debugowania. Używa pakietu debugowania, ten interfejs, można wyliczyć wszystkie konteksty kodu (lub kontekstu danych jednego) powiązany punkt przerwania, wywołując [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), która zwraca co najmniej jeden [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfejsów. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfejsu zwraca [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfejsu, a [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) zwraca [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Unii zawierająca kontekst kodu lub danych.  
  
 Jeśli nie można powiązać punkt przerwania jest DE, wysyła pojedynczy [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfejsu zdarzenia do pakietu debugowania. Debugowanie pakietu pobiera typ błędu (błąd lub ostrzeżenie) i komunikat informacyjny, wywołując [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), a następnie [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) i [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Spowoduje to zwrócenie [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) strukturę, która zawiera typ błędu i komunikatu.  
  
 Jeśli DE obsługuje punkt przerwania, ale nie można powiązać, zwracany jest błąd typu `BPET_TYPE_ERROR`. Debugowanie pakietu odpowiada wyświetlania okna dialogowego błędu, a następnie IDE umieszcza symbol wykrzyknika wewnątrz symbol punktu przerwania po lewej stronie wiersza kodu źródłowego.  
  
 Jeśli DE obsługuje punkt przerwania, nie można powiązać, lecz innej DE może powiązać go, zwracana jest ostrzeżenie. IDE odpowiada, umieszczając glif pytanie wewnątrz symbol punktu przerwania po lewej stronie wiersza kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
