---
title: IDebugCanStopEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5313595bd96b2176255822425d11776eedaedbe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942245"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Ten interfejs jest używany do zadania Menedżer debugowania sesji (SDM), czy można zatrzymać w bieżącej lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do obsługi krokowe wykonywanie kodu źródłowego. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu).  
  
 Implementację tego interfejsu muszą komunikować się wywołanie SDM [wartości właściwości CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) do aparatu debugowania. Na przykład, można to zrobić za pomocą wiadomości opublikowane w usłudze komunikatów aparatu debugowania wątku lub obiekt implementujący ten interfejs może zawierać odwołanie do aparatu debugowania i wywołania zwrotnego do aparatu debugowania przy użyciu flagi przekazywane do `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE może wysyłać ta metoda każdorazowo, gdy DE otrzyma monit o kontynuowanie wykonywania i DE jest krokowe wykonywanie kodu. To zdarzenie jest wysyłane za pomocą [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego dostarczonych przez model SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugCanStopEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Pobiera przyczynę tego zdarzenia.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Określa, czy debugowanego programu należy zatrzymać lokalizacji tego zdarzenia (oraz wysyłania zdarzenia opisujące przyczynę zatrzymywania) po prostu kontynuuj wykonywanie.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Pobiera kontekst dokumentu, opisująca lokalizację tego zdarzenia.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Pobiera kontekst kodu, który określa lokalizację tego zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 DE wysyła tego interfejsu, jeśli czynności użytkownika do funkcji i "de" wykryje żadnych informacji debugowania lub informacje o debugowaniu istnieje, ale DE nie wie, jeśli dla tej lokalizacji można wyświetlić kodu źródłowego.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)