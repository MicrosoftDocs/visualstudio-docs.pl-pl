---
title: IDebugThread2::GetLogicalThread | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718841"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Aparaty debugowania nie implementują tej metody.

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
[w] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt, który reprezentuje ramkę stosu.

`ppLogicalThread`\
[na zewnątrz] Zwraca `IDebugLogicalThread2` interfejs, który reprezentuje skojarzony wątek logiczny. Implementacja aparatu debugowania należy ustawić to na wartość null.

## <a name="return-value"></a>Wartość zwracana
 Implementacje aparatu debugowania zawsze zwracają `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
