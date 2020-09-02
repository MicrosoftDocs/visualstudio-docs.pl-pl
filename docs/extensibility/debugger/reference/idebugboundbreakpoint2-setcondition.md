---
title: 'IDebugBoundBreakpoint2:: setcondition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f23fbe1b353378ca521fa802bdeae25fd12476df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735459"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Ustawia lub zmienia warunek skojarzony z tym związanym punktem przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parametry
`bpCondition`\
podczas Wartość z wyliczenia [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , która opisuje warunek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` czy stan powiązanego obiektu punktu przerwania jest ustawiony na `BPS_DELETED` (część wyliczenia [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Uwagi
 Wszystkie warunki, które były wcześniej skojarzone z tym punktem przerwania, zostaną utracone.

## <a name="see-also"></a>Zobacz też
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
