---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb40c3b0d6d08e3b4b995d2f39440775df292f9f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013759"
---
# <a name="idebugmodule3"></a>IDebugModule3
Ten interfejs reprezentuje moduł, który obsługuje alternatywne lokalizacje symboli i JustMyCode stanów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs obsługuje alternatywne lokalizacje symboli i współpracować ze Stanami JustMyCode (zobacz [słownik debugera w usłudze Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) definicji "JustMyCode").  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [getsymbolsearchinfo —](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) zwraca ten interfejs. Wysyła DE [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) współpracować w celu Menedżer debugowania sesji (SDM) przy użyciu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody. Ponadto po wywołaniu [QueryInterface](/cpp/atl/queryinterface) na [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfejsu zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod na [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Zwraca listę ścieżek wyszukiwane symboli i wyniki wyszukiwania poszczególnych ścieżek.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Ładuje i inicjuje symbole dla bieżącego modułu.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Zwraca flagę, określania, czy moduł reprezentuje kod użytkownika.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Określa, czy moduł należy uznać za kod użytkownika lub nie.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio jest typowej tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)