---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be07e034b4059ae7ade40a5a248c01bc4a8237b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62924671"
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Wylicza prawidłowe wartości, które określają informacje do pobrania dotyczące żądania punktu przerwania. To wyliczenie rozszerza [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) wyliczenia.

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

#### <a name="parameters"></a>Parametry
Inicjowanie BPREQI90_BPLOCATION lub użyj `bpLocation` pola (lokalizacji punktu przerwania) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

Inicjowanie BPREQI90_LANGUAGE lub użyj `guidLanguage` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_PROGRAM lub użyj `pProgram` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_PROGRAMNAME lub użyj `bstrProgramName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_THREAD lub użyj `pThread` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_THREADNAME lub użyj `bstrThreadName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_PASSCOUNT lub użyj `bpPassCount` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_CONDITION lub użyj `bpCondition` pola (warunek punktu przerwania) `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_FLAGS lub użyj `dwFlags` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_ALLOLDFIELDS lub użyj wszystkich pól dla elementu `BP_REQUEST_INFO` struktury.

Inicjowanie BPREQI90_VENDOR lub użyj `guidVendor` pole `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_CONSTRAINT lub użyj `bstrConstraint` pole `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_TRACEPOINT lub użyj `bstrTracepoint` pole `BP_REQUEST_INFO2` struktury.

Inicjowanie BPREQI90_MACROTRACEPOINT lub użyj `bstrMacroTracepoint` pole `BP_REQUEST_INFO2` struktury. BPREQI_ALLFIELDS nie zawiera tego pola.

BPREQI90_ALLFIELDS określa wszystkie pola dla `BP_REQUEST_INFO2` struktury.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
