---
title: IDebugStackFrame2::GetDebugProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c520482d78b8630c639088ca98d66782f2e2d75
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321814"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Pobiera opis właściwości ramki stosu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>Parametry
`ppDebugProp`\
[out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który opisuje właściwości tej ramki stosu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywoływanie [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metody z odpowiednie filtry może pobrać zmienne lokalne, parametry metody, rejestrów i "to" wskaźnik ramki stosu.

## <a name="see-also"></a>Zobacz także
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)