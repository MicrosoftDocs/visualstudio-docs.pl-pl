---
title: IDebugObject::SetReferenceValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e861a67ada36bd25b30e08bf8a62163bceea979
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211301"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Ustawia wartość odwołanie do tego obiektu.

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
[in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt reprezentujący nową wartość odniesienia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda powoduje, że to [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) odwołanie do wartości obiektu w obiekcie `pObject` parametru wyrzuca dowolnego odwołania do poprzedniego. Uwaga że `IDebugObject` obiekt już musi być typem referencyjnym.

## <a name="see-also"></a>Zobacz także
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)