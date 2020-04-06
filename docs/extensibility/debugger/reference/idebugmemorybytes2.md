---
title: IDebugMemoryBytes2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727504"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Ten interfejs reprezentuje bajty pamięci.

## <a name="syntax"></a>Składnia

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania bajtów w pamięci.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zwraca ten interfejs, aby zapewnić dostęp do pamięci systemowej. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) i [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) zwracają ten interfejs, aby zapewnić dostęp do bajtów obiektu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugMemoryBytes2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Odczytuje sekwencję bajtów, zaczynając od danej lokalizacji.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapisuje `dwCount` bajty, `pStartContext`zaczynając od .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Pobiera rozmiar w bajtach pamięci reprezentowanej przez ten interfejs.|

## <a name="remarks"></a>Uwagi
 Dla właściwości interfejs [IDebugProperty2 reprezentujący](../../../extensibility/debugger/reference/idebugproperty2.md) tablicę `IDebugMemoryBytes2` zapewnia interfejs, aby uzyskać dostęp do wartości w tej tablicy.

 **Widok pamięci** programu Visual Studio wywołuje [GetMemoryBytes,](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) aby pobrać `IDebugMemoryBytes2` interfejs dostępu do pamięci systemowej. Adres, do który ma być dostępny, uzyskuje się przez analizowanie wyrażenia wprowadzonego jako adres w widoku pamięci, `IDebugProperty2` a następnie ocenianie analizowanego wyrażenia przy użyciu [programu EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) w celu uzyskania interfejsu. Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zwraca [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) który opisuje adres pamięci. Ten kontekst pamięci jest następnie przekazywany do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
