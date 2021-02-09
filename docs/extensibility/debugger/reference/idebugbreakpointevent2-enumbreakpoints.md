---
title: 'IDebugBreakpointEvent2:: EnumBreakpoints | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaf3cac6d49ef2d09a9952ac41b2bb36262fbc7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899036"
---
# <a name="idebugbreakpointevent2enumbreakpoints"></a>IDebugBreakpointEvent2::EnumBreakpoints
Tworzy moduł wyliczający dla wszystkich punktów przerwania, które są wywoływane w bieżącej lokalizacji kodu.

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
określoną Zwraca obiekt [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) , który wylicza wszystkie punkty przerwania skojarzone z bieżącą lokalizacją w kodzie.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nie wszystkie punkty przerwania w określonej lokalizacji mogą być uruchamiane w określonym czasie (na przykład punkt przerwania z warunkiem nie będzie wyzwalany do momentu spełnienia tego warunku).

## <a name="see-also"></a>Zobacz też
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
