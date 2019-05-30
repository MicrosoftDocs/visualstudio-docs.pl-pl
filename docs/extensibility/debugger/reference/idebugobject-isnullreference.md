---
title: IDebugObject::IsNullReference | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fb6b5c0692ec43feec0cf4de48d9ce730b0032e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323513"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Sprawdza, czy ten obiekt jest odwołanie o wartości null.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parametry
`pfIsNull`\
[out] Zwraca wartość różna od zera (`TRUE`) Jeśli ten obiekt jest odwołanie o wartości null; w przeciwnym razie zwraca wartość zero (`FALSE`).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Odwołanie o wartości null oznacza obiekt, który nie został przypisany do pustego obiektu.

## <a name="see-also"></a>Zobacz także
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)