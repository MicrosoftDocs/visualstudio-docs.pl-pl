---
description: Określa informacje do pobrania dla żądania punktu przerwania.
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc0d24d07f5c7473df7e963ee56ca6023fffa16d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067624"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Określa informacje do pobrania dla żądania punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Pola
`BPREQI_BPLOCATION`\
Zainicjuj/Użyj `bpLocation` pola (Lokalizacja punktu przerwania) struktury [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI_LANGUAGE`\
Zainicjuj lub Użyj `guidLanguage` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_PROGRAM`\
Zainicjuj lub Użyj `pProgram` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_PROGRAMNAME`\
Zainicjuj lub Użyj `bstrProgramName` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_THREAD`\
Zainicjuj lub Użyj `pThread` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_THREADNAME`\
Zainicjuj lub Użyj `bstrThreadName` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_PASSCOUNT`\
Zainicjuj lub Użyj `bpPassCount` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_CONDITION`\
Zainicjuj/Użyj `bpCondition` pola (warunek punktu przerwania) `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_FLAGS`\
Zainicjuj lub Użyj `dwFlags` pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktury lub.

`BPREQI_ALLOLDFIELDS`\
Zainicjuj/Użyj wszystkich pól dla `BP_REQUEST_INFO` struktury.

`BPREQI_VENDOR`\
Zainicjuj/Użyj `guidVendor` pola `BP_REQUEST_INFO2` struktury.

`BPREQI_CONSTRAINT`\
Zainicjuj/Użyj `bstrConstraint` pola `BP_REQUEST_INFO2` struktury.

`BPREQI_TRACEPOINT`\
Zainicjuj/Użyj `bstrTracepoint` pola `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLFIELDS`\
Określa wszystkie pola `BP_REQUEST_INFO2` struktury.

## <a name="remarks"></a>Uwagi
Przeszedł jako argument do [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) i metod [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , aby określić, które pola [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i struktur [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) mają być inicjowane.

Te flagi są również używane do wskazywania, które pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` struktur i są używane i są prawidłowe podczas zwracania każdej struktury.

Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
