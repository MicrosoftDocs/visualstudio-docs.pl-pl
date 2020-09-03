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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7080760b174c51d62c44cd2757944948e0104ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727734"
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
