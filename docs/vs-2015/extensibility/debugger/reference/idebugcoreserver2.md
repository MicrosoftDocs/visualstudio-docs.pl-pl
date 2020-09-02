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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192918"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs służy do reprezentowania i uzyskiwania informacji z serwera na komputerze w sieci.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio implementuje ten interfejs, aby reprezentować serwer. Każde wystąpienie programu Visual Studio tworzy wystąpienie tego interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Dostawca portu niestandardowego odbiera ten interfejs w wywołaniu [zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Aparat debugowania może uzyskać ten interfejs pośrednio za pośrednictwem wywołania metody [getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (która zwraca [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), interfejs, który jest pochodną `IDebugCoreServer2` ).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugCoreServer2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Pobiera nazwę i atrybuty maszyny.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Pobiera nazwę komputera.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Pobiera dostawcę portu, który istnieje na komputerze.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Pobiera port, który już istnieje na maszynie.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Tworzy moduł wyliczający dla wszystkich portów na komputerze.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Tworzy moduł wyliczający dla wszystkich dostawców portów na komputerze.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Pobiera narzędzia maszyny dla komputera.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest również używany przez program Visual Studio do przeglądania procesów uruchomionych na maszynach w sieci.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Wydarzen](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
