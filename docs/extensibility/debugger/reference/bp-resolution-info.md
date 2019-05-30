---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e07110a4ab4aae014f6134130a92dfcb8a31289
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350597"
---
# <a name="bpresolutioninfo"></a>BP_RESOLUTION_INFO
Opisuje informacje powiązany punkt przerwania dla punktu przerwania w kodzie lub punktu przerwania danych.

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
Kolekcja flagi z [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) wyliczenia, które określa pola, które są wypełnione.

`bpResLocation`\
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) strukturę, która określa lokalizację punktu przerwania w kodzie lub danych.

`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje aplikacji, w którym wystąpił błąd punktu przerwania.

`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, w którym jest uruchomiona aplikacja, która zawiera błąd punktu przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracany przez [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md).

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
