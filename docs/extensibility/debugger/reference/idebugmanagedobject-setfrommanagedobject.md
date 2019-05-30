---
title: IDebugManagedObject::SetFromManagedObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf82275bf3375098cc8a8bcbeb200846252d2cec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349376"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Ustawia wartość wystąpienia obiektu klasy wartości z instancji klasy wartości podać jako parametr.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Parametry
`pManagedObject`\
[in] Interfejs, który reprezentuje zarządzanego obiektu zawierającego nowe wartości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda służy do zmiany obiektu zarządzanego, reprezentowane przez [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) obiektu.

## <a name="see-also"></a>Zobacz także
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)