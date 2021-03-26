---
description: Ta metoda określa typ obiektu w czasie wykonywania.
title: 'IDebugBinder:: ResolveRuntimeType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23bc63e4550264d499c6d97a03aa9361b3fa4f62
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067351"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Ta metoda określa typ obiektu w czasie wykonywania.

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
podczas [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , który ma zostać rozwiązany.

`ppResolved`\
określoną Zwraca typ obiektu jako element [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Typ czasu wykonywania obiektu nie zawsze jest znany w czasie kompilacji. Na przykład przy użyciu polimorfizmu argument można przekazywać do funkcji jako jej klasy bazowej, takiej jak Klasa Button. Rzeczywisty argument może być klasą pochodną, taką jak Klasa przycisków radiowych.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
