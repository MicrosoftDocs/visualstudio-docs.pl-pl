---
title: IDebugMemoryBytes2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a9434f7464d4c13d0c4085a3ad195ba8b1bd2f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007584"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Ten interfejs reprezentuje bajtów pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania bajtów w pamięci.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zwraca ten interfejs, w celu zapewnienia dostępu do pamięci systemowej. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) i [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) zwraca ten interfejs, aby zapewnić dostęp do obiektu w bajtach.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugMemoryBytes2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Odczytuje sekwencji bajtów, zaczynając od danej lokalizacji.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapisuje `dwCount` bajty począwszy `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Pobiera rozmiar w bajtach, pamięci, reprezentowane przez ten interfejs.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku właściwości [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) udostępnia interfejs reprezentujący tablicę `IDebugMemoryBytes2` interfejsu, aby uzyskać dostęp do wartości w tablicy.  
  
 Visual Studio **widok pamięci** wywołania [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) można pobrać `IDebugMemoryBytes2` interfejs do uzyskiwania dostępu do pamięci systemowej. Adres, który ma być uzyskiwany dostęp jest uzyskiwany analizowania wyrażenia jako adres zawierana widok pamięci, a następnie dokonanie oceny oprogramowania przy użyciu wyrażenia przeanalizowany [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można pobrać `IDebugProperty2` interfejsu. Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zwraca [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) adres pamięci, który opisuje. Ten kontekst pamięci jest następnie przekazywany do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)