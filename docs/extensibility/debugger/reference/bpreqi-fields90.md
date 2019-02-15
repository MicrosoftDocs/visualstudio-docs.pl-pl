---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b9135ddc2f2fb1c45f9f4c9d31ff8fe5bfdb0ee
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316239"
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
BPREQI90_BPLOCATION  
Inicjowanie lub użyj `bpLocation` pola (lokalizacji punktu przerwania) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) lub [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

BPREQI90_LANGUAGE  
Inicjowanie lub użyj `guidLanguage` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_PROGRAM  
Inicjowanie lub użyj `pProgram` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_PROGRAMNAME  
Inicjowanie lub użyj `bstrProgramName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_THREAD  
Inicjowanie lub użyj `pThread` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_THREADNAME  
Inicjowanie lub użyj `bstrThreadName` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_PASSCOUNT  
Inicjowanie lub użyj `bpPassCount` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_CONDITION  
Inicjowanie lub użyj `bpCondition` pola (warunek punktu przerwania) `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_FLAGS  
Inicjowanie lub użyj `dwFlags` pole `BP_REQUEST_INFO` lub `BP_REQUEST_INFO2` struktury.

BPREQI90_ALLOLDFIELDS  
Inicjowanie lub użyj wszystkich pól z `BP_REQUEST_INFO` struktury.

BPREQI90_VENDOR  
Inicjowanie lub użyj `guidVendor` pole `BP_REQUEST_INFO2` struktury.

BPREQI90_CONSTRAINT  
Inicjowanie lub użyj `bstrConstraint` pole `BP_REQUEST_INFO2` struktury.

BPREQI90_TRACEPOINT  
Inicjowanie lub użyj `bstrTracepoint` pole `BP_REQUEST_INFO2` struktury.

BPREQI90_MACROTRACEPOINT  
Inicjowanie lub użyj `bstrMacroTracepoint` pole `BP_REQUEST_INFO2` struktury. BPREQI_ALLFIELDS nie zawiera tego pola.

BPREQI90_ALLFIELDS  
Określa wszystkie pola dla `BP_REQUEST_INFO2` struktury.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
