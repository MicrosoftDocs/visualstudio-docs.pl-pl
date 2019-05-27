---
title: IDebugObject::GetMemoryContext | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce66c4274aa00b7a75376aa4411c11241468ea5b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202915"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Pobiera kontekst pamięci, która reprezentuje adres wartość obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Parametry
`pContext`\
[out] Zwraca [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt reprezentujący adres wartość obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst zwracany pamięci określa adres wartości, reprezentowane przez to [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektu.

## <a name="see-also"></a>Zobacz także
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)