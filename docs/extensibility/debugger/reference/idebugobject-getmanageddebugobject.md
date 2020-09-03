---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726692"
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
