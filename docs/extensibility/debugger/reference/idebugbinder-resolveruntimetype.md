---
title: IDebugBinder::ResolveRuntimeType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2954b5f2a1ac4dd14485a1b924423ba53fddcb7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315166"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Ta metoda określa typu run-time obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Parametry
`pObject`\
[in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zostać rozpoznane.

`ppResolved`\
[out] Zwraca typ obiektu jako [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zawsze typu run-time obiektu nie jest znany w czasie kompilacji. Na przykład za pomocą polimorfizm, argument można przekazać do funkcji jako swojej klasy bazowej, takie jak klasa przycisków. Rzeczywisty argument może być klasy pochodnej, takich jak klasa przycisków radiowych.

## <a name="see-also"></a>Zobacz także
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)