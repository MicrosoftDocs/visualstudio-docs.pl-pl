---
title: IDebugThread2::GetLogicalThread | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4273d1c8bff6f07fdcf12b5b324d8d42eb08799
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199712"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Aparaty debugowania nie należy implementować tej metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Parametry
`pStackFrame`\
[in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt, który reprezentuje ramkę stosu.

`ppLogicalThread`\
[out] Zwraca `IDebugLogicalThread2` interfejs, który reprezentuje skojarzony wątek logiczne. Implementacja aparatu debugowania, należy Ustaw tę opcję na wartość null.

## <a name="return-value"></a>Wartość zwracana
 Debuguj aparat implementacje zwracana zawsze `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)