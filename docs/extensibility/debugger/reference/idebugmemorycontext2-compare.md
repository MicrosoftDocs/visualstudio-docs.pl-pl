---
title: IDebugMemoryContext2::Porównaj | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727492"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Porównuje kontekst pamięci do każdego kontekstu w danej tablicy w sposób wskazany przez porównać flagi, zwracając indeks pierwszego kontekstu, który pasuje.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Parametry
`compare`\
[w] Wartość z [wyliczenia CONTEXT_COMPARE,](../../../extensibility/debugger/reference/context-compare.md) która określa typ porównania.

`rgpMemoryContextSet`\
[w] Tablica odwołań do [obiektów IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) do porównania.

`dwMemoryContextSetLen`\
[w] Liczba kontekstów w `rgpMemoryContextSet` tablicy.

`pdwMemoryContext`\
[na zewnątrz] Zwraca indeks pierwszego kontekstu pamięci, który spełnia porównania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca, `E_COMPARE_CANNOT_COMPARE` jeśli nie można porównać dwóch kontekstów.

## <a name="remarks"></a>Uwagi
 Aparat debugowania (DE) nie musi obsługiwać wszystkich typów porównań, `CONTEXT_EQUAL` `CONTEXT_LESS_THAN`ale `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE`musi obsługiwać co najmniej , i .

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
