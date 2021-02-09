---
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29756b3be6d2c46d39b581dd3db0af61bfaa18f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878932"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Usuwa określony wyjątek, dlatego nie jest już obsługiwany przez aparat debugowania.

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
podczas Struktura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , która opisuje wyjątek, który ma zostać usunięty.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Usuwany wyjątek musi być wcześniej ustawiony przez wcześniejsze wywołanie metody [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Aby usunąć wszystkie wyjątki jednocześnie, wywołaj metodę [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
