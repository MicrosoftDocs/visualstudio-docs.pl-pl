---
title: IDebugMemoryBytes2::WriteAt | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727517"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Zapisuje określoną liczbę bajtów pamięci, zaczynając od określonego adresu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parametry
`pStartContext`\
[w] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa, gdzie można rozpocząć pisanie bajtów.

`dwCount`\
[w] Liczba bajtów do zapisania.

`rgbMemory`\
[w] Bajty do zapisu. Przyjmuje się, że ta `dwCount` tablica ma rozmiar co najmniej bajtów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym `S_FALSE` razie zwraca, jeśli nie wszystkie bajty mogą `E_FAIL`być zapisywane lub zwraca kod błędu (zazwyczaj).

## <a name="remarks"></a>Uwagi
 Jeśli adres początkowy nie znajduje się w oknie pamięci reprezentowanym przez ten obiekt [IDebugMemoryBytes2,](../../../extensibility/debugger/reference/idebugmemorybytes2.md) nie występuje zapis i `E_FAIL` zwracany jest kod błędu — nawet jeśli kwota zapisu nakłada się na miejsce w pamięci.

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
