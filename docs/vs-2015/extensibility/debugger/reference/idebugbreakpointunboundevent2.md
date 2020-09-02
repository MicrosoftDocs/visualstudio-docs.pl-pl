---
title: IDebugBreakpointUnboundEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 93897047af0408a3908600015724fca3ffa2d2d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65673779"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs informuje Menedżera debugowania sesji (SDM) o anulowaniu powiązania przerwania z załadowanego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs w ramach obsługi punktów przerwania. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs (model SDM używa [metody QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) do uzyskiwania dostępu do `IDebugEvent2` interfejsu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Element DE tworzy i wysyła ten obiekt Event, gdy powiązany punkt przerwania został anulowany. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez model SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugBreakpointUnboundEvent2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Pobiera punkt przerwania, który stał się niepowiązany.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Pobiera przyczynę powiązania punktu przerwania.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas zwalniania biblioteki DLL lub klasy aparatu debugowania wszystkie punkty przerwania, które zostały powiązane z kodem w tym module, muszą być anulowane względem debugowanego programu. `IDebugBreakpointUnboundEvent2`Jest wysyłany dla każdego niepowiązanego punktu przerwania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
