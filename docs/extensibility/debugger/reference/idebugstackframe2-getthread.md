---
title: IDebugStackFrame2::GetThread | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetThread
helpviewer_keywords:
- IDebugStackFrame2::GetThread
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99248291ce06aa4f07f627429bbb5cc2993a61c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916001"
---
# <a name="idebugstackframe2getthread"></a>IDebugStackFrame2::GetThread
Pobiera wątek skojarzony z ramki stosu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetThread ( 
   IDebugThread2** ppThread
);
```

```csharp
int GetThread ( 
   out IDebugThread2 ppThread
);
```

#### <a name="parameters"></a>Parametry
 `ppThread`

 [out] Zwraca [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)