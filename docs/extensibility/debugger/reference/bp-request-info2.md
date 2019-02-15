---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a953d367acd90ed869316e2595e5a8c666e816a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316863"
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
`dwFields`  
Kombinacja flag z [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) wyliczenia, która określa pola, które są wypełnione.

`guidLanguage`  
Identyfikator GUID języka.

`bpLocation`  
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) strukturę, która określa typ lokalizacji punktu przerwania.

`pProgram`  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje aplikacji, w której występuje punkt przerwania.

`bstrProgramName`  
Nazwa aplikacji, w której występuje punkt przerwania.

`pThread`  
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, w której występuje punkt przerwania.

`bstrThreadName`  
Nazwa wątku, w której występuje punkt przerwania.

`bpCondition`  
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) strukturę, która opisuje warunki, na których zostanie uruchomiony punkt przerwania.

`bpPassCount`  
[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która zawiera informacje o liczby — dostęp próbny dla punktu przerwania.

`dwFlags`  
Kombinacja flag z [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) wyliczenie, które określa flagi dla żądanego punktu przerwania.

`guidVendor`  
Identyfikator GUID dostawcy. Może być wartością null.

`bstrConstraint`  
Nazwa ograniczenia punktu przerwania. Może być wartością null.

`bstrTracepoint`  
Nazwa punktu śledzenia. Może być wartością null.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracany przez [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)  
[BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)  
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)  
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
