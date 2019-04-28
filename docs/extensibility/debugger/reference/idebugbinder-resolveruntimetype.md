---
title: IDebugBinder::ResolveRuntimeType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1d4622e1de76406568cda4761005c5482f3169d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877500"
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

#### <a name="parameters"></a>Parametry
 `pObject`

 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zostać rozpoznane.

 `ppResolved`

 [out] Zwraca typ obiektu jako [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zawsze typu run-time obiektu nie jest znany w czasie kompilacji. Na przykład za pomocą polimorfizm, argument można przekazać do funkcji jako swojej klasy bazowej, takie jak klasa przycisków. Rzeczywisty argument może być klasy pochodnej, takich jak klasa przycisków radiowych.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)