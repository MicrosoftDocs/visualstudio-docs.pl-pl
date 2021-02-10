---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d56acb3efecc794e38430511dfeb2a84cd62de0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949600"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
Opisuje powiązane informacje o punkcie przerwania dla punktu przerwania kodu lub punktu przerwania danych.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>Elementy członkowskie
`dwFields`\
Kolekcja flag z wyliczeń [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) , które określają, które pola są wypełniane.

`bpResLocation`\
Struktura [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , która określa lokalizację punktu przerwania w kodzie lub danych.

`pProgram`\
Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje aplikację, w której wystąpił błąd punktu przerwania.

`pThread`\
Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje wątek, w którym działa aplikacja, która zawiera błąd punktu przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana przez [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md).

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
