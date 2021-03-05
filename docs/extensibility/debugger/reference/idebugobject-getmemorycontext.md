---
description: Pobiera kontekst pamięci, który reprezentuje adres wartości obiektu.
title: 'IDebugObject:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9fabcee7bc0f4501f1440345b648fb93dab84d16
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172115"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Pobiera kontekst pamięci, który reprezentuje adres wartości obiektu.

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
określoną Zwraca obiekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) reprezentujący adres wartości obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwrócony kontekst pamięci określa adres wartości reprezentowanej przez ten obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
