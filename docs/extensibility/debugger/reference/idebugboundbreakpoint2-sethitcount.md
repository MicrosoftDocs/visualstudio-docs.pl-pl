---
title: IDebugBoundBreakpoint2::SetHitCount | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac7cbfa337bfdcf54d213b299badc9ca56d8dcba
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716314"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Ustawia liczbę trafień dla powiązany punkt przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

#### <a name="parameters"></a>Parametry
 `dwHitCount`

 [in] Liczba trafień, aby ustawić.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` Jeśli stan obiektu powiązany punkt przerwania jest ustawiony na `BPS_DELETED` (część [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) wyliczenia).

## <a name="remarks"></a>Uwagi
 Liczba trafień jest liczba przypadków, gdy ten punkt przerwania ma wywoływane podczas wykonywania bieżącej sesji.

 Ta metoda jest zazwyczaj wywoływana przez aparat debugowania, aby zaktualizować bieżące liczba trafień w tym punkcie przerwania.

## <a name="see-also"></a>Zobacz też
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)