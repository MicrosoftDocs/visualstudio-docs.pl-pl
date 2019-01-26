---
title: IDebugProgramEngines2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a383dc55b42fe8baad8df31628d0a182d50d554e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025673"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Ten interfejs jest używany przez węzły programu do określenia wszystkich możliwych silniki debugowania (DE), które można debugować ten program.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE lub dostawcy niestandardowego portu implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) umożliwiających ustanawianie określonych DE do użycia dla określonego programu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgramNode2` interfejsu w celu uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProgramEngines2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Wskazuje wszystkie możliwe DEs, który można debugować ten program.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wybiera DE używane do debugowania tego programu.|  
  
## <a name="remarks"></a>Uwagi  
 Po DE jest wybierany przez użytkownika, wybór jest zarejestrowany w węźle programu poprzez wywołanie [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Wybrany aparat staje się aparat, który został zwrócony przez [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)