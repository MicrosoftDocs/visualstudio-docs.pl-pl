---
title: IDebugObject2::GetAlias | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c72182b497e2b24d41a784c405d169c3db195f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726287"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Pobiera alias skojarzony z tym obiektem, jeśli istnieje.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametry
`ppAlias`\
[na zewnątrz] Zwraca obiekt [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) reprezentujący alias tego obiektu; w przeciwnym razie zwraca wartość null.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Alias obiektu jest tworzony za pomocą wywołania [metody CreateAlias.](../../../extensibility/debugger/reference/idebugobject2-createalias.md)

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
