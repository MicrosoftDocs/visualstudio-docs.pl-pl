---
description: Aparaty debugowania nie implementują tej metody.
title: 'IDebugThread2:: GetLogicalThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9193cde20ba1035552451143c676aab291d7c684
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168351"
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
podczas Obiekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , który reprezentuje ramkę stosu.

`ppLogicalThread`\
określoną Zwraca `IDebugLogicalThread2` interfejs, który reprezentuje skojarzony wątek logiczny. Implementacja aparatu debugowania powinna ustawiać tę wartość na null.

## <a name="return-value"></a>Wartość zwracana
 Implementacje aparatu debugowania zawsze zwracają `E_NOTIMPL` .

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
