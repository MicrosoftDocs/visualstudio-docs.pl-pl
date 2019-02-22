---
title: IDebugObject::IsProxy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 037245524446ded2ec250f1d4a04e21bf5924a61
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678426"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Określa, czy obiekt przezroczystym serwerem proxy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

#### <a name="parameters"></a>Parametry
 `pfIsProxy`

 [out] `TRUE` Jeśli obiekt jest przezroczystym serwerem proxy; w przeciwnym razie `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest implementowana przez domyślny aparat debugowania języka C++.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)