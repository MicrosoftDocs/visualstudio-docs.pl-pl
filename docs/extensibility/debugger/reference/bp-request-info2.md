---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737880"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Zawiera informacje wymagane do zaimplementowania punktu przerwania, w tym identyfikator GUID dostawcy, ograniczenie i punkt śledzenia.

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
Kombinacja flag z wyliczenia [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) , która określa, które pola są wypełniane.

`guidLanguage`\
Identyfikator GUID języka.

`bpLocation`\
Struktura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) , która określa typ lokalizacji punktu przerwania.

`pProgram`\
Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje aplikację, w której występuje punkt przerwania.

`bstrProgramName`\
Nazwa aplikacji, w której występuje punkt przerwania.

`pThread`\
Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje wątek, w którym występuje punkt przerwania.

`bstrThreadName`\
Nazwa wątku, w którym występuje punkt przerwania.

`bpCondition`\
Struktura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) opisująca warunki, w których zostanie uruchomiony punkt przerwania.

`bpPassCount`\
Struktura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , która zawiera informacje o liczbie przebiegu punktu przerwania.

`dwFlags`\
Kombinacja flag z wyliczenia [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) , która określa flagi dla żądanego punktu przerwania.

`guidVendor`\
Identyfikator GUID dostawcy. Może być wartością null.

`bstrConstraint`\
Nazwa ograniczenia punktu przerwania. Może być wartością null.

`bstrTracepoint`\
Nazwa punktu śledzenia. Może być wartością null.

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana przez metodę [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
