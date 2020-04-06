---
title: IDebugBinder::GetFunctionObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01d501367f47e520e9170118da8b6fdfcb326137
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736010"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Ta metoda pobiera [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiektu używanego do tworzenia parametrów funkcji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parametry
`ppFunction`\
[na zewnątrz] Zwraca interfejs [IDebugFunctionObject,](../../../extensibility/debugger/reference/idebugfunctionobject.md) który jest używany do tworzenia parametrów funkcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
