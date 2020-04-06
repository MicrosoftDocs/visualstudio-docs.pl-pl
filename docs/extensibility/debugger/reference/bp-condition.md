---
title: BP_CONDITION | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88ed6b6468c5765c8f987c1f15f3e4e8ade9c8c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738107"
---
# <a name="bp_condition"></a>BP_CONDITION
Opisuje warunki, w których punkt przerwania jest uruchamiany.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Elementy członkowskie
`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje aktywny wątek dla aplikacji, która zawiera punkt przerwania.

`styleCondition`\
Wartość z [wyliczenia BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) opisujące styl tego warunku punktu przerwania.

`bstrContext`\
Lokalizacja punktu przerwania.

`bstrCondition`\
Stan wypalania punktu przerwania.

`nRadix`\
radix do wykorzystania przy ocenie jakichkolwiek informacji liczbowych.

## <a name="remarks"></a>Uwagi
Struktura ta jest członkiem [struktur BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Ta struktura jest również przekazywana jako parametr do [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) i [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
