---
title: IDebugBreakpointEvent2::EnumBreakpoints | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a74e726951297802b2e47c3501c083ac83ffa2a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352913"
---
# <a name="idebugbreakpointevent2enumbreakpoints"></a>IDebugBreakpointEvent2::EnumBreakpoints
Tworzy moduł wyliczający dla wszystkich punktów przerwania, które są uruchamiane w bieżącej lokalizacji kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumBreakpoints(
  IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBreakpoints(
  out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Zwraca [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) obiekt, który wylicza wszystkie punkty przerwania skojarzony z bieżącą lokalizacją kodu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nie wszystkie punkty przerwania w danej lokalizacji może wyzwalać w określonym czasie (na przykład punkt przerwania z warunkiem nie zostanie uruchomiony do momentu spełnienia warunku).

## <a name="see-also"></a>Zobacz także
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)