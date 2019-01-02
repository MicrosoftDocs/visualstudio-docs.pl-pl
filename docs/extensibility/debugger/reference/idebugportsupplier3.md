---
title: IDebugPortSupplier3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b058324bfe0dcde4b2285c1a7478859ed27131b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825987"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Ten interfejs umożliwia obiekt wywołujący określić, czy dostawcy portu można zachować portów (zapisując je na dysku) między wywołań debugera, a następnie Pobierz listę portów zachowanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego portu implementuje ten interfejs obsługuje przechowywanie ani portu informacje są zapisywane na dysku. Ten interfejs musi zostać wdrożone na tym samym obiekcie jako [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) na `IDebugPortSupplier2` interfejsu w celu uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod odziedziczone [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfejs, ten interfejs obsługuje następujące czynności:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Zwraca, czy dostawca portu można utrwalić portów (zapisując je na dysku) między wywołań debugera.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Zwraca obiekt, który może służyć do wyliczenia za pośrednictwem wszystkich portów, które były zapisywane na dysku przez dostawcę tego portu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dostawcy portu można utrwalić porty różnych wywołań, powinien implementować ten interfejs. Porty powinien być ładowany podczas dostawcy portu jest tworzone i zapisywane na dysku, kiedy niszczony jest dostawcy portu.  
  
 Aparat debugowania zazwyczaj nie wchodzi w interakcję z dostawcą portu, a także będą ma być używana dla tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)