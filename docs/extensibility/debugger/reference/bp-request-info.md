---
description: Zawiera informacje wymagane do zaimplementowania punktu przerwania.
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40c88d1c07d3610ff6d098fbbf8517476cc07103
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059655"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Zawiera informacje wymagane do zaimplementowania punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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

## <a name="remarks"></a>Uwagi
Ta struktura jest zwracana przez metodę [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .

Jeśli musisz uzyskać identyfikator GUID dostawcy aparatu debugowania, ograniczenie punktu przerwania lub punkt śledzenia, zobacz strukturę [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
