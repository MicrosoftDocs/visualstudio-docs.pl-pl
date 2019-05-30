---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8f9c601cf1620d002bd86b8bc110d28bdb533e61
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352945"
---
# <a name="bprequestinfo2"></a>BP_REQUEST_INFO2
Zawiera informacje wymagane do zaimplementowania punkt przerwania, w tym identyfikator GUID dostawcy, ograniczenia i śledzenia.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Elementy członkowskie
`dwFields`\
Kombinacja flag z [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) wyliczenia, która określa pola, które są wypełnione.

`guidLanguage`\
Identyfikator GUID języka.

`bpLocation`\
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) strukturę, która określa typ lokalizacji punktu przerwania.

`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje aplikacji, w której występuje punkt przerwania.

`bstrProgramName`\
Nazwa aplikacji, w której występuje punkt przerwania.

`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, w której występuje punkt przerwania.

`bstrThreadName`\
Nazwa wątku, w której występuje punkt przerwania.

`bpCondition`\
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) strukturę, która opisuje warunki, na których zostanie uruchomiony punkt przerwania.

`bpPassCount`\
[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która zawiera informacje o liczby — dostęp próbny dla punktu przerwania.

`dwFlags`\
Kombinacja flag z [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) wyliczenie, które określa flagi dla żądanego punktu przerwania.

`guidVendor`\
Identyfikator GUID dostawcy. Może być wartością null.

`bstrConstraint`\
Nazwa ograniczenia punktu przerwania. Może być wartością null.

`bstrTracepoint`\
Nazwa punktu śledzenia. Może być wartością null.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracany przez [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
