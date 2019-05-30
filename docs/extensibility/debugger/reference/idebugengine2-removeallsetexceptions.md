---
title: IDebugEngine2::RemoveAllSetExceptions | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17063a2c503535bc20b61ba8d9914fc54005cccc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352616"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Usuwa listy wyjątków, ustawionych przez środowisko IDE dla określonej architektury środowiska wykonawczego lub języka.

## <a name="syntax"></a>Składnia

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>Parametry
`guidType`\
[in] Identyfikator GUID dla języka lub identyfikator GUID dla aparatu debugowania, które są specyficzne dla architektury środowiska wykonawczego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Usunięto przez tę metodę wyjątki były ustawione przez poprzednie wywołania do [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) metody.

 Aby usunąć określony wyjątek, należy wywołać [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)