---
title: IDebugPendingBreakpoint2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba1c2da0bd43d6c5a0d7ad78bb974e9c987e1432
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736074"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje punkt przerwania, który jest gotowy do powiązania do lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługę punktów przerwania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) tworzy oczekujący punkt przerwania z [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfejsu. Wywołanie [powiązać](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) tworzy `IDebugBreakpoint2` interfejs, który reprezentuje powiązany punkt przerwania w programie.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugPendingBreakpoint2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy ten oczekujący punkt przerwania można powiązać z lokalizacji kodu.|  
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Tworzy powiązanie ten oczekujący punkt przerwania z jedną lub więcej lokalizacji kodu.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan to oczekujące punktu przerwania.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie przerwania, który został użyty do utworzenia tego oczekujący punkt przerwania.|  
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Włącza/wyłącza zwirtualizowane stan to oczekujące punktu przerwania.|  
|[Enable](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Włącza/wyłącza włączony stan to oczekujące punktu przerwania.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Ustawia lub zmienia warunek skojarzonego z tą oczekującą punktu przerwania.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Ustawia lub zmienia liczba — dostęp próbny skojarzonego z tą oczekującą punktu przerwania.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania, powiązany z tym oczekujący punkt przerwania.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów, które powstały w wyniku ten oczekujący punkt przerwania.|  
|[Delete](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa ten oczekujący punkt przerwania i wszystkie punkty przerwania, powiązany z niego.|  
  
## <a name="remarks"></a>Uwagi  
 `IDebugPendingBreakpoint2` można traktować jako dostawca wszystkie niezbędne informacje potrzebne do powiązania punktu przerwania do kodu, który można zastosować do jednego lub wielu programów.  
  
 Oczekujący punkt przerwania może potencjalnie wygenerować więcej niż jeden powiązany punkt przerwania. Na przykład punkt przerwania w szablonie styl C++ może utworzyć powiązany punkt przerwania dla poszczególnych unikatowych wystąpień tego szablonu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)

