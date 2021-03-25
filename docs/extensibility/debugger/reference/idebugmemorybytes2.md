---
description: Ten interfejs reprezentuje bajty pamięci.
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b18b4575780966d9ad34fa6c5638a89274d52c3c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058641"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Ten interfejs reprezentuje bajty pamięci.

## <a name="syntax"></a>Składnia

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować bajty w pamięci.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zwraca ten interfejs, aby zapewnić dostęp do pamięci systemowej. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) i [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) zwracają ten interfejs, aby zapewnić dostęp do bajtów obiektu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugMemoryBytes2` .

|Metoda|Opis|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Odczytuje sekwencję bajtów, rozpoczynając od danej lokalizacji.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapisuje `dwCount` bajty, rozpoczynając od `pStartContext` .|
|[GetSize —](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Pobiera rozmiar (w bajtach) pamięci reprezentowanej przez ten interfejs.|

## <a name="remarks"></a>Uwagi
 W przypadku właściwości Interfejs [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) reprezentujący tablicę zapewnia `IDebugMemoryBytes2` interfejs do uzyskiwania dostępu do wartości w tej tablicy.

 Wywołania **widoku pamięci** programu Visual Studio [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) do pobrania `IDebugMemoryBytes2` interfejsu w celu uzyskania dostępu do pamięci systemowej. Adres, do którego uzyskuje się dostęp, jest uzyskiwany przez analizę wyrażenia wprowadzonego jako adres w widoku pamięci, a następnie obliczenie wyrażenia przeanalizowanego za pomocą [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , aby uzyskać `IDebugProperty2` interfejs. Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zwraca [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , który opisuje adres pamięci. Ten kontekst pamięci jest następnie przekazanie do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
