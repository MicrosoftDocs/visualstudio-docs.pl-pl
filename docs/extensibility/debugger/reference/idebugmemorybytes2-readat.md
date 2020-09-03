---
title: 'IDebugMemoryBytes2:: ReadAt | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727536"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Odczytuje sekwencję bajtów, rozpoczynając od danej lokalizacji.

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
podczas Obiekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , który określa miejsce rozpoczęcia odczytywania bajtów.

`dwCount`\
podczas Liczba bajtów do odczytania. Określa także długość `rgbMemory` tablicy.

`rgbMemory`\
[in. out] Tablica wprowadzona w bajtach rzeczywiście odczytanych.

`pdwRead`\
określoną Zwraca liczbę bajtów, które faktycznie są odczytywane.

`pdwUnreadable`\
[in. out] Zwraca liczbę bajtów, które nie są odczytywane. Może być wartością null, jeśli klient jest nieoprocentowany w liczbie bajtów, które nie są odczytywane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli żądanie 100 bajtów i pierwsze 50 są możliwe do odczytu, następne 20 nie są czytelne, a pozostałe 30 są odczytywane, Metoda ta zwraca:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 W takim przypadku `*pdwRead + *pdwUnreadable < dwCount` obiekt wywołujący musi wykonać dodatkowe wywołanie w celu odczytania pozostałych 30 bajtów oryginalnego 100, a obiekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , który przeszedł w `pStartContext` parametrze, musi być zaawansowany przez 70.

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
