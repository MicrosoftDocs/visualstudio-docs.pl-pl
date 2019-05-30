---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58967be9befc7061ea8005009b1628966a93de0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349503"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Wywołuje się, gdy przetwarzanie przechwycone wyjątku zostało zakończone.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Parametry
`pqwCookie`\
[out] Unikatowa wartość, która jest skojarzona z wyjątku, który został przechwycony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po [interceptcurrentexception —](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) metoda zakończeniu obsługi wyjątku przechwycone wysyła [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) zdarzeń. Można użyć programu obsługi `GetInterceptCookie` metodę, która pobierze unikatową wartość skojarzony z wyjątkiem (taką samą wartość przekazywana do `InterceptCurrentException` metody).

## <a name="see-also"></a>Zobacz także
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)