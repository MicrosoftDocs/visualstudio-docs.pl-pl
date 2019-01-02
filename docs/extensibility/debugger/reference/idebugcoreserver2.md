---
title: IDebugCoreServer2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33347f985f1c495e61e097e04890ca6931751331
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921760"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Ten interfejs jest używany do reprezentowania i uzyskiwania informacji z serwera na komputerze w sieci.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio implementuje ten interfejs do reprezentowania serwera. Każde wystąpienie programu Visual Studio tworzy wystąpienie tego interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Dostawcy niestandardowego portu otrzyma ten interfejs w wywołaniu [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Aparat debugowania można uzyskać ten interfejs pośrednio poprzez wywołanie [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (co powoduje zwrócenie [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), interfejs, który jest tworzony na podstawie `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugCoreServer2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Pobiera nazwę i atrybuty maszyny.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Pobiera nazwę maszyny.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Pobiera dostawcy portu, która istnieje na maszynie.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Pobiera portu, która już istnieje na maszynie.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Tworzy moduł wyliczający wszystkie porty na maszynie.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Tworzy moduł wyliczający dla wszystkich dostawców port na komputerze.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Pobiera narzędzia maszyny dla maszyny.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest również używany przez program Visual Studio do przeglądania procesów uruchomionych na komputerach w sieci.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)