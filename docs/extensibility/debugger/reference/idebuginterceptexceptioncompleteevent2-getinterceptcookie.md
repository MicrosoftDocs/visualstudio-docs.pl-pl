---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 400f0c6785a9cf9096caba9403886a2009905859
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700981"
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

#### <a name="parameters"></a>Parametry
 `pqwCookie`

 [out] Unikatowa wartość, która jest skojarzona z wyjątku, który został przechwycony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po [interceptcurrentexception —](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) metoda zakończeniu obsługi wyjątku przechwycone wysyła [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) zdarzeń. Można użyć programu obsługi `GetInterceptCookie` metodę, która pobierze unikatową wartość skojarzony z wyjątkiem (taką samą wartość przekazywana do `InterceptCurrentException` metody).

## <a name="see-also"></a>Zobacz też
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)