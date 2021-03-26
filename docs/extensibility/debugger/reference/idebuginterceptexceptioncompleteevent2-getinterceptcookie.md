---
description: Wywoływana po zakończeniu przetwarzania przechwyconego wyjątku.
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52c0cdf514f606287386c68713371d112cb97e79
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091919"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Wywoływana po zakończeniu przetwarzania przechwyconego wyjątku.

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
określoną Unikatowa wartość skojarzona z wyjątkiem, który został przechwycony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po zakończeniu obsługi przechwyconego wyjątku przez metodę [InterceptCurrentException —](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) wysyła zdarzenie [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) . Program obsługi może użyć `GetInterceptCookie` metody do pobrania unikatowej wartości skojarzonej z wyjątkiem (ta sama wartość jest przenoszona do `InterceptCurrentException` metody).

## <a name="see-also"></a>Zobacz też
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
