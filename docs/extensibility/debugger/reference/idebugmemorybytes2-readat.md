---
title: IDebugMemoryBytes2::ReadAt | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1083239dbb00e5b953fe7a72c27a350ffe34cc2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314299"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Odczytuje sekwencji bajtów, zaczynając od danej lokalizacji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Parametry
`pStartContext`\
[in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa, gdzie należy rozpocząć odczyt bajtów.

`dwCount`\
[in] Liczba bajtów do odczytania. Również określa długość `rgbMemory` tablicy.

`rgbMemory`\
[out w] Tablica wypełniona Bajty odczytane.

`pdwRead`\
[out] Zwraca liczbę bajtów ciągłych odczytane.

`pdwUnreadable`\
[out w] Zwraca liczbę bajtów nie można go odczytać. Może być wartością null, jeśli klient jest zainteresowany liczbę bajtów nie można go odczytać.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli wymagane są 100 bajtów i 50 pierwszych można odczytać, następnych 20 są nieczytelne i pozostałe 30 do odczytu, Metoda ta zwraca:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 W tym przypadku ponieważ `*pdwRead + *pdwUnreadable < dwCount`, obiekt wywołujący musi wywoływania dodatkowych odczytu pozostałe bajty 30 oryginalnego 100, żądane i [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt przekazany w `pStartContext` parametru musi być zaawansowane za 70.

## <a name="see-also"></a>Zobacz także
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)