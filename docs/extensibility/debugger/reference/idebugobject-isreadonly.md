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
ms.openlocfilehash: bef21a491a175e7f1a7f93cd7c8d9d70a5ec6279
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682625"
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

#### <a name="parameters"></a>Parametry
 `pfIsReadOnly`

 [out] Zwraca wartość różna od zera (`TRUE`) Jeśli ten obiekt jest tylko do odczytu; w przeciwnym razie, zwraca wartość zero (`FALSE`).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obiekt tylko do odczytu nie może mieć wartość ulegnie zmianie po jego utworzeniu.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)