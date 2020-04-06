---
title: IDebugMemoryBytes2::ReadAt | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727536"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Odczytuje sekwencję bajtów, zaczynając od danej lokalizacji.

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
[w] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa, gdzie rozpocząć odczyt bajtów.

`dwCount`\
[w] Liczba bajtów do odczytania. Określa również długość tablicy. `rgbMemory`

`rgbMemory`\
[w, na zewnątrz] Tablica wypełniona bajtami faktycznie odczytywany.

`pdwRead`\
[na zewnątrz] Zwraca liczbę ciągłych bajtów faktycznie odczytanych.

`pdwUnreadable`\
[w, na zewnątrz] Zwraca liczbę nieczytelnych bajtów. Może być wartością null, jeśli klient nie jest zainteresowany liczbą nieczytelnych bajtów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli wymagane jest 100 bajtów, a pierwsze 50 jest czytelne, następne 20 jest nieczytelne, a pozostałe 30 jest czytelne, ta metoda zwraca:

 *`pdwRead`= 50

 *`pdwUnreadable`= 20

 W takim przypadku, ponieważ `*pdwRead + *pdwUnreadable < dwCount`obiekt wywołujący musi wykonać dodatkowe wywołanie, aby odczytać pozostałe 30 bajtów oryginalnego 100 żądane i [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt przekazany w parametrze `pStartContext` musi być zaawansowany przez 70.

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
