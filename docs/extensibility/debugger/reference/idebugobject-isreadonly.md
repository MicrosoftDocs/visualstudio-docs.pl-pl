---
title: IDebugObject::IsReadOnly | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e3c01e3cf6ccf7eef23f7a357bbd12e739224a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211368"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Określa, czy ten obiekt tylko do odczytu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parametry
`pfIsReadOnly`\
[out] Zwraca wartość różna od zera (`TRUE`) Jeśli ten obiekt jest tylko do odczytu; w przeciwnym razie, zwraca wartość zero (`FALSE`).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obiekt tylko do odczytu nie może mieć wartość ulegnie zmianie po jego utworzeniu.

## <a name="see-also"></a>Zobacz także
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)