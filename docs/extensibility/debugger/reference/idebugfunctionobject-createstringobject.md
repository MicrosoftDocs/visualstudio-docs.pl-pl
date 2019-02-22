---
title: IDebugFunctionObject::CreateStringObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0dd79223d3b51195e9f45490cc8aa95c10aca8e8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689905"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Tworzy obiekt ciągu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

#### <a name="parameters"></a>Parametry
 `pcstrString`

 [in] Wartość ciągu z obiektem ciągu.

 `ppObject`

 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt, który reprezentuje obiekt ciągu nowo utworzony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje ciąg, który jest parametr do funkcji, która jest reprezentowana przez [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu.

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)