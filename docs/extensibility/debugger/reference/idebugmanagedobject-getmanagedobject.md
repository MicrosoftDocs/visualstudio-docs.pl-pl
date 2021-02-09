---
title: 'IDebugManagedObject:: getmanagedobject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18cb56b083386c3ac8358a101c1d52fb14cb39ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890243"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Zwraca interfejs, który reprezentuje obiekt zarządzany.

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

## <a name="parameters"></a>Parametry
`ppManagedObject`\
określoną Zwraca interfejs, który reprezentuje obiekt zarządzany.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Interfejs zwracany przez tę metodę może być badany dla dowolnego interfejsu zaimplementowanego przez klasę zarządzaną, umożliwiając wywoływanie jego metod.

## <a name="see-also"></a>Zobacz też
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
