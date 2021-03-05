---
description: Porównuje kontekst pamięci z każdym kontekstem w danej tablicy w sposób wskazany przez porównanie flag, zwracając indeks pierwszego kontekstu, który jest zgodny.
title: 'IDebugMemoryContext2:: Compare | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f21b22574a780f5e9fcfa045c6786b13d82caa45
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165101"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Porównuje kontekst pamięci z każdym kontekstem w danej tablicy w sposób wskazany przez porównanie flag, zwracając indeks pierwszego kontekstu, który jest zgodny.

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
podczas Wartość z wyliczenia [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) , która określa typ porównania.

`rgpMemoryContextSet`\
podczas Tablica odwołań do obiektów [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , względem których ma zostać wykonane porównanie.

`dwMemoryContextSetLen`\
podczas Liczba kontekstów w `rgpMemoryContextSet` tablicy.

`pdwMemoryContext`\
określoną Zwraca indeks pierwszego kontekstu pamięci, który spełnia porównanie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_COMPARE_CANNOT_COMPARE` czy nie można porównać dwóch kontekstów.

## <a name="remarks"></a>Uwagi
 Aparat debugowania (de) nie musi obsługiwać wszystkich typów porównań, ale musi obsługiwać co najmniej `CONTEXT_EQUAL` , `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` i `CONTEXT_SAME_SCOPE` .

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
