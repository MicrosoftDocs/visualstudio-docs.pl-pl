---
title: BP_LOCATION_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737942"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Określa typ lokalizacji punktu przerwania dla żądania punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Pola
`BPLT_NONE`\
Określa lokalizację punktu przerwania.

`BPLT_FILE_LINE`\
Określa typ lokalizacji punktu przerwania jako wiersz pliku.

`BPLT_FUNC_OFFSET`\
Określa typ lokalizacji punktu przerwania jako przesunięcie funkcji.

`BPLT_CONTEXT`\
Określa typ lokalizacji punktu przerwania jako kontekst.

`BPLT_STRING`\
Określa typ lokalizacji punktu przerwania jako ciąg.

`BPLT_ADDRESS`\
Określa typ lokalizacji punktu przerwania jako adres.

`BPLT_RESOLUTION`\
Określa typ lokalizacji punktu przerwania jako rozdzielczość.

`BPLT_CODE_FILE_LINE`\
Określa typ lokalizacji punktu przerwania jako wiersz kodu źródłowego.

`BPLT_CODE_FUNC_OFFSET`\
Określa typ lokalizacji punktu przerwania jako przesunięcie funkcji kodu.

`BPLT_CODE_CONTEXT`\
Określa typ lokalizacji punktu przerwania jako kontekst kodu.

`BPLT_CODE_STRING`\
Określa typ lokalizacji punktu przerwania jako ciąg kodu.

`BPLT_CODE_ADDRESS`\
Określa typ lokalizacji punktu przerwania jako adres kodu.

`BPLT_DATA_STRING`\
Określa typ lokalizacji punktu przerwania jako ciąg danych.

`BPLT_TYPE_MASK`\
Określa maskę bitową, dzięki czemu typ punktu przerwania może zostać wyodrębniony z wartości.

`BPLT_LOCATION_TYPE_MASK`\
Określa maskę bitową, dzięki czemu typ lokalizacji punktu przerwania może zostać wyodrębniony z wartości.

## <a name="remarks"></a>Uwagi
Przekazany jako parametr do [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) metody.

Typ lokalizacji punktu przerwania składa się z typu punktu przerwania i typu lokalizacji. Oznacza to, że typ lokalizacji punktu przerwania nigdy nie `BPT_CODE`jest tylko typem punktu `BPLT_FILE_LINE`przerwania (na przykład) lub typem lokalizacji (na przykład). Wstępnie zdefiniowane stałe dla wszystkich typów lokalizacji punktu przerwania obecnie obsługiwanych są`BPLT_CODE_FILE_LINE` `BPLT_DATA_STRING`uwzględnione w tym wyliczeniu (przez ).

`BPT_CODE`i `BPT_DATA` są członkami wyliczenia [BP_TYPE.](../../../extensibility/debugger/reference/bp-type.md)

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
