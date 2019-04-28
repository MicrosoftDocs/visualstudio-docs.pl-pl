---
title: IDebugObject::GetManagedDebugObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6738c70b75ff1e2f393b59e330ce57f2232de61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918531"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Tworzy kopię obiektu zarządzanego w przestrzeni adresowej aparatu debugowania.

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

#### <a name="parameters"></a>Parametry
 `ppObject`

 [out] Zwraca [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) obiekt reprezentujący nowo utworzonego obiektu zarządzanego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nie reprezentuje wystąpienie klasy zarządzanej wartości.

## <a name="remarks"></a>Uwagi
 To [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektu musi reprezentować wartość zarządzanego wystąpienia klasy, takie jak `System.Decimal` wystąpienia. Dzięki kopii lokalnej obciążenie związane z wywołaniem [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) wyeliminowania.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)