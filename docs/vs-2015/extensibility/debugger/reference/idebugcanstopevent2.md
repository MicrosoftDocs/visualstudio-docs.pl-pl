---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f8e92ecd6e99f9fe369157c92dd4d964f86da97a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766669"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest używany do zadania Menedżer debugowania sesji (SDM), czy można zatrzymać w bieżącej lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do obsługi krokowe wykonywanie kodu źródłowego. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) dostęp do `IDebugEvent2` interfejsu).  
  
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
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
