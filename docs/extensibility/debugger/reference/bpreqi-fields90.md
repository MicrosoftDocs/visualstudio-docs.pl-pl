---
title: BPREQI_FIELDS90 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737733"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Wylicza prawidłowe wartości, które określają informacje, które mają być pobierane o żądaniu punktu przerwania. To wyliczenie rozszerza wyliczenie [BPREQI_FIELDS.](../../../extensibility/debugger/reference/bpreqi-fields.md)

## <a name="syntax"></a>Składnia

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Pola
`BPREQI90_BPLOCATION`\
Zainicjować lub `bpLocation` użyć pola (lokalizacja punktu przerwania) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

`BPREQI90_LANGUAGE`\
Zainicjować lub `guidLanguage` użyć pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` lub struktury.

`BPREQI90_PROGRAM`\
Zainicjować lub `pProgram` użyć pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` lub struktury.

`BPREQI90_PROGRAMNAME`\
Zainicjować lub `bstrProgramName` użyć pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` lub struktury.

`BPREQI90_THREAD`\
Zainicjować lub `pThread` użyć pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` lub struktury.

`BPREQI90_THREADNAME`\
Zainicjować lub `bstrThreadName` użyć pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` lub struktury.

`BPREQI90_PASSCOUNT`\
Zainicjować lub `bpPassCount` użyć pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` lub struktury.

`BPREQI90_CONDITION`\
Zainicjować lub `bpCondition` użyć pola (warunek punktu `BP_REQUEST_INFO` `BP_REQUEST_INFO2` przerwania) lub struktury.

`BPREQI90_FLAGS`\
Zainicjować lub `dwFlags` użyć pola `BP_REQUEST_INFO` `BP_REQUEST_INFO2` lub struktury.

`BPREQI90_ALLOLDFIELDS`\
Zainicjować lub użyć wszystkich pól `BP_REQUEST_INFO` dla struktury.

`BPREQI90_VENDOR`\
Zainicjować lub `guidVendor` użyć `BP_REQUEST_INFO2` pola struktury.

`BPREQI90_CONSTRAINT`\
Zainicjować lub `bstrConstraint` użyć `BP_REQUEST_INFO2` pola struktury.

`BPREQI90_TRACEPOINT`\
Zainicjować lub `bstrTracepoint` użyć `BP_REQUEST_INFO2` pola struktury.

`BPREQI90_MACROTRACEPOINT`\
Zainicjować lub `bstrMacroTracepoint` użyć `BP_REQUEST_INFO2` pola struktury. BPREQI_ALLFIELDS nie obejmuje tego pola.

`BPREQI90_ALLFIELDS`\
Określa wszystkie pola `BP_REQUEST_INFO2` dla struktury.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
