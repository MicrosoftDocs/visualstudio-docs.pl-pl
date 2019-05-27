---
title: IDebugObject::GetValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e6fd1d3b4d7effe0f4c6f5f0434a01422345f00
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202878"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Pobiera wartość obiektu jako serię kolejnych bajtów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parametry
`pValue`\
[out w] Tablica, która jest wypełniane serię kolejnych bajtów reprezentujący wartość obiektu.

`nSize`\
[in] Maksymalna liczba bajtów do pobrania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Pobierz całkowitą liczbę bajtów wartości, które mogą być pobierane przez wywołanie metody [getsize —](../../../extensibility/debugger/reference/idebugobject-getsize.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)