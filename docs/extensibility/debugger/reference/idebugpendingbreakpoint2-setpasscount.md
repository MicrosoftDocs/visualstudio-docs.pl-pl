---
title: IDebugPendingBreakpoint2::SetPassCount | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5af01702c20b4841c5d737bef2c3be7f885cc31e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340565"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Ustawia lub zmienia liczba — dostęp próbny skojarzone z Oczekujący punkt przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parametry
`bpPassCount`\
[in] A [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która zawiera liczbę — dostęp próbny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` Jeśli punkt przerwania został usunięty.

## <a name="remarks"></a>Uwagi
 Dowolnej liczbie — dostęp próbny, który był wcześniej skojarzony z Oczekujący punkt przerwania zostaną utracone. Wszystkie punkty przerwania, powiązany z tym oczekujących punktów przerwania są wywoływane w celu ich liczby — dostęp próbny równa `bpPassCount` parametru.

## <a name="see-also"></a>Zobacz także
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)