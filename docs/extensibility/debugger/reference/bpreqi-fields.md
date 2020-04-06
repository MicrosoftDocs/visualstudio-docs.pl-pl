---
title: BPREQI_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737745"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Określa informacje, które mają być pobierane o żądaniu punktu przerwania.

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
Inicjowanie/używanie pola `bpLocation` (lokalizacja punktu przerwania) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

`BPREQI_LANGUAGE`\
Zainicjować/użyć `guidLanguage` pola `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_PROGRAM`\
Zainicjować/użyć `pProgram` pola `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_PROGRAMNAME`\
Zainicjować/użyć `bstrProgramName` pola `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_THREAD`\
Zainicjować/użyć `pThread` pola `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_THREADNAME`\
Zainicjować/użyć `bstrThreadName` pola `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_PASSCOUNT`\
Zainicjować/użyć `bpPassCount` pola `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_CONDITION`\
Zainicjować/użyć `bpCondition` pola (warunek punktu przerwania) `BP_REQUEST_INFO` pola lub `BP_REQUEST_INFO2` struktury.

`BPREQI_FLAGS`\
Zainicjować/użyć `dwFlags` pola `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLOLDFIELDS`\
Inicjuj/użyj wszystkich `BP_REQUEST_INFO` pól dla struktury.

`BPREQI_VENDOR`\
Zainicjować/użyć `guidVendor` pola `BP_REQUEST_INFO2` struktury.

`BPREQI_CONSTRAINT`\
Zainicjować/użyć `bstrConstraint` pola `BP_REQUEST_INFO2` struktury.

`BPREQI_TRACEPOINT`\
Zainicjować/użyć `bstrTracepoint` pola `BP_REQUEST_INFO2` struktury.

`BPREQI_ALLFIELDS`\
Określa wszystkie pola `BP_REQUEST_INFO2` dla struktury.

## <a name="remarks"></a>Uwagi
Przekazywane jako argument do [Metody GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) i [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) aby określić, które pola [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktur mają zostać zainicjowane.

Flagi te są również używane do `BP_REQUEST_INFO` `BP_REQUEST_INFO2` wskazania, które pola i struktury są używane i prawidłowe, gdy każda struktura jest zwracana.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
