---
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d51e0fc895c104c1a18ef079c6784384e4cedbb4
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316694"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
W tym artykule opisano, liczbę i warunki, na których jest uruchamiany warunkowego punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Elementy członkowskie
`dwPassCount`  
Liczba razy, aby przekazać za pośrednictwem punktu przerwania przed wyzwoleniem go.

`stylePassCount`  
Wartość z zakresu od [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) Liczba przebiegów wyliczenie, które określa styl punkt przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest elementem członkowskim [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury.

Ta struktura również jest przekazywany jako parametr do[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) i[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)  
[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)  
[BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
