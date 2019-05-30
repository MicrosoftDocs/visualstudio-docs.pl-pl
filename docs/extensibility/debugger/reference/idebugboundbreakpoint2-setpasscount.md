---
title: IDebugBoundBreakpoint2::SetPassCount | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee0032a079ff9c67e0a2de350e0405cfa20303db
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314509"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Ustawia lub zmienia liczba — dostęp próbny skojarzony ten powiązany punkt przerwania.

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
[in] [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która określa liczbę — dostęp próbny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` Jeśli stan obiektu powiązany punkt przerwania jest ustawiony na `BPS_DELETED` (część [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) wyliczenia).

## <a name="remarks"></a>Uwagi
 Count — dostęp próbny Określa, kiedy punkt przerwania jest uruchamiany. Bieżący przebieg lub liczba trafień można uzyskać przez wywołanie metody [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) metody.

 Dowolnej liczbie — dostęp próbny, który był wcześniej skojarzony z tego punktu przerwania zostaną utracone.

## <a name="see-also"></a>Zobacz także
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)