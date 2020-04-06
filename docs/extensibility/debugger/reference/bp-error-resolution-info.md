---
title: BP_ERROR_RESOLUTION_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738085"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Opisuje rozpoznawanie punktu przerwania błędu, w tym lokalizacji, programu i wątku.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Elementy członkowskie
`dwFields`\
Kombinacja wartości z wyliczenia [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) określająca, które pola tej struktury są wypełniane.

`bpResLocation`\
Unia [BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) która określa lokalizację rozpoznawania punktów przerwania.

`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje aplikację, w której wystąpił błąd punktu przerwania.

`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, na którym jest uruchomiona aplikacja, która wygenerowała błąd punktu przerwania.

`bstrMessage`\
Ciąg zawierający wszelkie ostrzeżenia lub komunikat o błędzie wynikające z tej rozdzielczości błędu.

`dwType`\
Wartość z [wyliczenia BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) określająca typ błędu punktu przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana z [Metody GetResolutionInfo.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
