---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
podczas Obiekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , który reprezentuje ramkę stosu.

`ppLogicalThread`\
określoną Zwraca `IDebugLogicalThread2` interfejs, który reprezentuje skojarzony wątek logiczny. Implementacja aparatu debugowania powinna ustawiać tę wartość na null.

## <a name="return-value"></a>Wartość zwracana
 Implementacje aparatu debugowania zawsze zwracają `E_NOTIMPL` .

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
