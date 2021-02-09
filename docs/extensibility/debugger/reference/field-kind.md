---
title: FIELD_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a18739ebe30a41e9dca837287d58db57795f878b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874372"
---
# <a name="field_kind"></a>FIELD_KIND
Określa rodzaj pola zawartego w obiekcie [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Składnia

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>Pola
`FIELD_KIND_TYPE`\
Wskazuje, że pole jest tylko typu.

`FIELD_KIND_SYMBOL`\
Wskazuje, że pole jest symbolem, z typem, nazwą i innymi informacjami.

`FIELD_TYPE_PRIMITIVE`\
Wskazuje, że pole jest typem danych pierwotnych.

`FIELD_TYPE_STRUCT`\
Wskazuje, że pole jest strukturą.

`FIELD_TYPE_CLASS`\
Wskazuje, że pole jest klasą.

`FIELD_TYPE_INTERFACE`\
Wskazuje, że pole jest interfejsem.

`FIELD_TYPE_UNION`\
Wskazuje, że pole jest Unią.

`FIELD_TYPE_ARRAY`\
Wskazuje, że pole jest tablicą.

`FIELD_TYPE_METHOD`\
Wskazuje, że pole jest metodą.

`FIELD_TYPE_BLOCK`\
Wskazuje, że pole jest blokiem.

`FIELD_TYPE_POINTER`\
Wskazuje, że pole jest wskaźnikiem.

`FIELD_TYPE_ENUM`\
Wskazuje, że pole jest wyliczanym typem danych.

`FIELD_TYPE_LABEL`\
Wskazuje, że pole jest etykietą.

`FIELD_TYPE_TYPEDEF`\
Wskazuje, że pole jest elementem TypeDef.

`FIELD_TYPE_BITFIELD`\
Wskazuje, że pole jest pole bitowe.

`FIELD_TYPE_NAMESPACE`\
Wskazuje, że pole jest przestrzenią nazw.

`FIELD_TYPE_MODULE`\
Wskazuje, że pole jest modułem.

`FIELD_TYPE_DYNAMIC`\
Wskazuje, że pole jest dynamiczne.

`FIELD_TYPE_PROP`\
Wskazuje, że pole jest właściwością.

`FIELD_TYPE_INNERCLASS`\
Wskazuje, że pole jest klasą wewnętrzną.

`FIELD_TYPE_REFERENCE`\
Wskazuje, że pole jest odwołaniem.

`FIELD_TYPE_EXTENDED`\
Zarezerwowane do użytku w przyszłości.

`FIELD_SYM_MEMBER`\
Wskazuje, że pole jest członkiem.

`FIELD_SYM_LOCAL`\
Wskazuje, że pole jest lokalne.

`FIELD_SYM_PARAMETER`\
Wskazuje, że pole jest parametrem.

`FIELD_SYM_THIS`\
Wskazuje, że pole jest wskaźnikiem "This".

`FIELD_SYM_GLOBAL`\
Wskazuje, że pole jest globalne.

`FIELD_SYM_PROP_GETTER`\
Wskazuje, że pole pobiera właściwości.

`FIELD_SYM_PROP_SETTER`\
Wskazuje, że pole ustawia właściwości.

`FIELD_SYM_EXTENDED`\
Zarezerwowane do użytku w przyszłości.

`FIELD_KIND_MASK`\
Wskazuje maskę dla rodzajów pól.

`FIELD_TYPE_MASK`\
Wskazuje maskę dla typów pól.

`FIELD_SYM_MASK`\
Wskazuje maskę dla informacji o symbolach.

## <a name="remarks"></a>Uwagi
Zwrócone z wywołania metody [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) .

W zależności od rodzaju pola funkcja [QueryInterface](/cpp/atl/queryinterface) może być wywoływana w interfejsie [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) w celu uzyskania bardziej szczegółowej formy interfejsu. Na przykład jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_METHOD` , można wywołać metodę `QueryInterface` na I `DebugField` uzyskać Interfejs [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
