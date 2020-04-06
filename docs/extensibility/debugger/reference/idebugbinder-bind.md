---
title: IDebugBinder::Bind | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a783025c96053a89956a1c77d46b5e417938a2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736019"
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
[w] [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) który zawiera element `pField`podrzędny, do którego odwołuje się .

`pField`\
[w] [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) który reprezentuje symbol.

`ppObject`\
[na zewnątrz] Zwraca `IDebugObject` to, co reprezentuje wystąpienie symbolu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
