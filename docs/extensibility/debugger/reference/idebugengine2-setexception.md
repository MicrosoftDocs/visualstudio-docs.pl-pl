---
title: IDebugEngine2::SetException | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2234c0c0b571e763d3b143b5606fe61c43f25cde
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352533"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Określa, jak aparat debugowania (DE) powinna obsługiwać dany wyjątek.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametry
`pException`\
[in] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury, który opisuje wyjątek i jak go debugować.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 DE może być zobowiązany do zatrzymać program generuje wyjątek w pierwszej szansy, drugiej szansy, lub wcale.

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)