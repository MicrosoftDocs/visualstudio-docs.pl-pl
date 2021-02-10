---
title: 'IDebugBinder:: getfunctionobject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7128c97c60b5743ea9759a9449b82e4e909a686
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939035"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Ta metoda pobiera obiekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) używany do tworzenia parametrów funkcji.

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
określoną Zwraca interfejs [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , który jest używany do tworzenia parametrów funkcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
