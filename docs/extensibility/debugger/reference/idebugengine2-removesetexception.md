---
title: IDebugEngine2::RemoveSetException | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45c3cec5ab0511ea80a6b04d9b3ee575afd9d149
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352546"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Usuwa określony wyjątek, więc nie jest już obsługiwane przez aparat debugowania.

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
[in] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury, który opisuje wyjątek, który ma zostać usunięty.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wyjątek usuwany musi zostały ustawione wcześniej przez wcześniejsze wywołanie [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) metody.

 Aby usunąć wszystkie wyjątki zestawu tylko raz, należy wywołać [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)