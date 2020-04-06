---
title: BP_PASSCOUNT | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3177ff093aea9a6f52465bd606b22883249d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737901"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Opisuje liczbę i warunki, na których warunkowy punkt przerwania jest uruchamiany.

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
`dwPassCount`\
Liczba razy, aby przejść przez punkt przerwania przed odpaleniem go.

`stylePassCount`\
Wartość z [wyliczenia BP_PASSCOUNT_STYLE,](../../../extensibility/debugger/reference/bp-passcount-style.md) która określa styl liczby przebiegów punktu przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest członkiem [struktury BP_REQUEST_INFO.](../../../extensibility/debugger/reference/bp-request-info.md)

Ta struktura jest również przekazywana jako parametr do[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) i[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
