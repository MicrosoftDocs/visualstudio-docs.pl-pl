---
title: IDebugProgram2::GetDebugProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 109e3ac1267afb4097429aafc9264416f3c2dbf1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319368"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Pobiera właściwości tego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parametry
`ppProperty`\
[out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje właściwości tego programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Właściwości zwracanego przez tę metodę są specyficzne dla programu. Jeśli program musi zwrócić więcej niż jedną właściwość, a następnie [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu zwróconego przez tę metodę jest kontenerem dodatkowe właściwości i wywoływania [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metoda zwraca Lista wszystkich właściwości.

 Program może narazić dowolną liczbę i rodzaj dodatkowe właściwości, które można opisać za pośrednictwem `IDebugProperty2` interfejsu. Środowisko IDE może wyświetlić właściwości dodatkowy program za pomocą interfejsu użytkownika przeglądarki właściwości ogólnych.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)