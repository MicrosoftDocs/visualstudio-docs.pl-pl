---
description: Ustawia wartość referencyjną tego obiektu.
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a65c14d4122ac6d877573822b4fa8be1cb6cdd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054117"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Ustawia wartość referencyjną tego obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parametry
`pObject`\
podczas Obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nową wartość referencyjną.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda sprawia, że obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) odwołuje się do wartości obiektu podaną w `pObject` parametrze, zwracając wszystkie poprzednie odwołanie. Należy pamiętać, że ten `IDebugObject` obiekt musi już być typem referencyjnym.

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
