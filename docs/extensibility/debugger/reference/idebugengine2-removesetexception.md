---
title: IDebugEngine2::RemoveSetException | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e811ce2e387c299ff3655799bf35185c1d2029b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730923"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Usuwa określony wyjątek, dzięki czemu nie jest już obsługiwany przez aparat debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametry
`pException`\
[w] Struktura [EXCEPTION_INFO,](../../../extensibility/debugger/reference/exception-info.md) która opisuje wyjątek do usunięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wyjątek usuwany musi być wcześniej ustawiony przez wcześniejsze wywołanie [Metody SetException.](../../../extensibility/debugger/reference/idebugengine2-setexception.md)

 Aby usunąć wszystkie wyjątki zestawu naraz, wywołaj [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
