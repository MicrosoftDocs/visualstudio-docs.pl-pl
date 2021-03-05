---
description: Tworzy kopię zarządzanego obiektu w przestrzeni adresowej aparatu debugowania.
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 87956b3630f9d152ecdda7754623e7257cf0a01a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164772"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Tworzy kopię zarządzanego obiektu w przestrzeni adresowej aparatu debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
określoną Zwraca obiekt [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) reprezentujący nowo utworzony obiekt zarządzany.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli ten [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nie reprezentuje wystąpienia klasy wartości zarządzanej.

## <a name="remarks"></a>Uwagi
 Ten obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) musi reprezentować wystąpienie klasy wartości zarządzanej, takie jak `System.Decimal` wystąpienie. Posiadanie kopii lokalnej powoduje wyeliminowanie narzutu na wywołanie funkcji [szacowania](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
