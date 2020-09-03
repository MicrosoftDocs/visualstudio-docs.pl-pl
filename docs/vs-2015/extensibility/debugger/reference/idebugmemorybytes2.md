---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e23588e8da41b981f372210def65fa34a7e55bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180547"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje bajty pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować bajty w pamięci.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zwraca ten interfejs, aby zapewnić dostęp do pamięci systemowej. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) i [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) zwracają ten interfejs, aby zapewnić dostęp do bajtów obiektu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugMemoryBytes2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Odczytuje sekwencję bajtów, rozpoczynając od danej lokalizacji.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapisuje `dwCount` bajty, rozpoczynając od `pStartContext` .|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Pobiera rozmiar (w bajtach) pamięci reprezentowanej przez ten interfejs.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku właściwości Interfejs [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) reprezentujący tablicę zapewnia `IDebugMemoryBytes2` interfejs do uzyskiwania dostępu do wartości w tej tablicy.  
  
 Wywołania **widoku pamięci** programu Visual Studio [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) do pobrania `IDebugMemoryBytes2` interfejsu w celu uzyskania dostępu do pamięci systemowej. Adres, do którego uzyskuje się dostęp, jest uzyskiwany przez analizę wyrażenia wprowadzonego jako adres w widoku pamięci, a następnie obliczenie wyrażenia przeanalizowanego za pomocą [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , aby uzyskać `IDebugProperty2` interfejs. Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zwraca [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , który opisuje adres pamięci. Ten kontekst pamięci jest następnie przekazanie do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
