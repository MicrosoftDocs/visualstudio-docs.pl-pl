---
description: Ustawia lub zmienia warunek skojarzony z oczekującym punktem przerwania.
title: 'IDebugPendingBreakpoint2:: setcondition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3cf12bce424e523702da92b86e8894a54ce58b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076605"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Ustawia lub zmienia warunek skojarzony z oczekującym punktem przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parametry
`bpCondition`\
podczas Struktura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , która określa warunek do ustawienia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wszystkie warunki, które wcześniej były skojarzone z oczekującym punktem przerwania, zostaną utracone. Wszystkie punkty przerwania powiązane z tym oczekującym punktem przerwania są wywoływane, aby ustawić ich warunek na wartość określoną w `bpCondition` parametrze.

## <a name="see-also"></a>Zobacz też
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
