---
title: IDebugManagedObject::GetManagedObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6df3a4f69c62e7681eade705186c802a225f060
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873390"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Zwraca interfejs, który reprezentuje obiektu zarządzanego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

#### <a name="parameters"></a>Parametry
 `ppManagedObject`

 [out] Zwraca interfejs, który reprezentuje obiektu zarządzanego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Interfejs zwrócone w wyniku tej metody można wykonywać zapytania, dla dowolnego interfejsu implementowany przez klasy zarządzanej, dzięki czemu jego metody do wywołania.

## <a name="see-also"></a>Zobacz też
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)