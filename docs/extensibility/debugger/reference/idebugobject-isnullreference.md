---
title: IDebugObject::IsNullReference | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25de5fdde9e0d834b98f09d2f5c9e2444f8a9d0e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706902"
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

#### <a name="parameters"></a>Parametry
 `pfIsNull`

 [out] Zwraca wartość różna od zera (`TRUE`) Jeśli ten obiekt jest odwołanie o wartości null; w przeciwnym razie zwraca wartość zero (`FALSE`).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Odwołanie o wartości null oznacza obiekt, który nie został przypisany do pustego obiektu.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)