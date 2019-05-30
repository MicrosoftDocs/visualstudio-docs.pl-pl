---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 757b8bfeeed2a7d75f3a0b4203b80b464e5b39fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350505"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
Określa informacje, które mają zostać pobrane o żądaniu punktu przerwania.

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
Inicjowanie bądź użyj `bpLocation` pola (lokalizacji punktu przerwania) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

`BPREQI_LANGUAGE`\
Inicjowanie bądź użyj `guidLanguage` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_PROGRAM`\
Inicjowanie bądź użyj `pProgram` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_PROGRAMNAME`\
Inicjowanie bądź użyj `bstrProgramName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_THREAD`\
Inicjowanie bądź użyj `pThread` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_THREADNAME`\
Inicjowanie bądź użyj `bstrThreadName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_PASSCOUNT`\
Inicjowanie bądź użyj `bpPassCount` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_CONDITION`\
Inicjowanie bądź użyj `bpCondition` pola (warunek punktu przerwania) `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_FLAGS`\
Inicjowanie bądź użyj `dwFlags` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLOLDFIELDS`\
Inicjowanie bądź Użyj wszystkich pól z `BP_REQUEST_INFO` struktury.

`BPREQI_VENDOR`\
Inicjowanie bądź użyj `guidVendor` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_CONSTRAINT`\
Inicjowanie bądź użyj `bstrConstraint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_TRACEPOINT`\
Inicjowanie bądź użyj `bstrTracepoint` pole `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLFIELDS`\
Określa wszystkie pola dla `BP_REQUEST_INFO2` struktury.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) i [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) metody, aby określić które pola [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) struktury mają zostać zainicjowane.

Te flagi są również używane w celu wskazania, które pola `BP_REQUEST_INFO` i `BP_REQUEST_INFO2` struktury są używane i ważne, gdy każda struktura jest zwracany.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
