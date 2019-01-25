---
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759637"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
