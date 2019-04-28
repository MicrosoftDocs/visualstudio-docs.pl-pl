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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1301c3ecde243e212bdeed3c8aca1a56f1cbc15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872079"
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

#### <a name="parameters"></a>Parametry
 `bpPassCount`

 [in] A [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która zawiera liczbę — dostęp próbny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` Jeśli punkt przerwania został usunięty.

## <a name="remarks"></a>Uwagi
 Dowolnej liczbie — dostęp próbny, który był wcześniej skojarzony z Oczekujący punkt przerwania zostaną utracone. Wszystkie punkty przerwania, powiązany z tym oczekujących punktów przerwania są wywoływane w celu ich liczby — dostęp próbny równa `bpPassCount` parametru.

## <a name="see-also"></a>Zobacz też
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)