---
title: BP_ERROR_RESOLUTION_INFO | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d89a871abf6a62dec712ce9d9ae486496c775b8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691205"
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
W tym artykule opisano rozwiązania punktu przerwania błędu, takie jak lokalizacja, program i wątku.

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
`dwFields` Kombinacja wartości z [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) wyliczenie opisujące są wypełnione pola, które tej struktury.

`bpResLocation` [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Unii, który określa lokalizację rozwiązania punktu przerwania.

`pProgram` [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje aplikacji, w którym wystąpił błąd punktu przerwania.

`pThread` [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku, na którym działa aplikacja, która wygenerowała błąd punktu przerwania.

`bstrMessage` Ciąg zawierający wszystkie komunikaty ostrzeżeń lub błędów wynikających z rozwiązania tego błędu.

`dwType` Wartość z zakresu od [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) wyliczenie, który określa typ błąd punktu przerwania.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana z [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
