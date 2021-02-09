---
title: 'IDebugBinder:: bind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ee9f303223da15bc75adbf31d533848fb017bb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901908"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Ta metoda pobiera kontekst pamięci lub obiekt, który zawiera bieżącą wartość symbolu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`pContainer`\
podczas [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , który zawiera element podrzędny, do którego się odwołuje `pField` .

`pField`\
podczas [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , który reprezentuje symbol.

`ppObject`\
określoną Zwraca wartość `IDebugObject` reprezentującą wystąpienie symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
