---
title: FIELD_MODIFIERS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5589b1535fbe22f0b0c1f2f9c9e34f70a4e7e861
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874325"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
Określa Modyfikatory dla typu pola.

## <a name="syntax"></a>Składnia

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>Pola
`FIELD_MOD_ACCESS_TYPE`\
Wskazuje, że nie można uzyskać dostępu do pola.

`FIELD_MOD_ACCESS_PUBLIC`\
Wskazuje, że pole ma dostęp publiczny.

`FIELD_MOD_ACCESS_PROTECTED`\
Wskazuje, że pole ma chroniony dostęp.

`FIELD_MOD_ACCESS_PRIVATE`\
Wskazuje, że pole ma dostęp prywatny.

`FIELD_MOD_NOMODIFIERS`\
Wskazuje, że pole nie ma modyfikatorów.

`FIELD_MOD_STATIC`\
Wskazuje, że pole jest statyczne.

`FIELD_MOD_CONSTANT`\
Wskazuje, że pole jest stałą.

`FIELD_MOD_TRANSIENT`\
Wskazuje, że pole jest przejściowe.

`FIELD_MOD_VOLATILE`\
Wskazuje, że pole jest nietrwałe.

`FIELD_MOD_ABSTRACT`\
Wskazuje, że pole jest abstrakcyjne.

`FIELD_MOD_NATIVE`\
Wskazuje, że pole jest natywne.

`FIELD_MOD_SYNCHRONIZED`\
Wskazuje, że pole jest zsynchronizowane.

`FIELD_MOD_VIRTUAL`\
Wskazuje, że pole jest wirtualne.

`FIELD_MOD_INTERFACE`\
Wskazuje, że pole jest interfejsem.

`FIELD_MOD_FINAL`\
Wskazuje, że pole jest końcowe.

`FIELD_MOD_SENTINEL`\
Wskazuje, że pole jest wskaźnikiem.

`FIELD_MOD_INNERCLASS`\
Wskazuje, że pole jest klasą wewnętrzną.

`FIELD_TYPE_OPTIONAL`\
Wskazuje, że pole jest opcjonalne.

`FIELD_MOD_BYREF`\
Wskazuje, że pole jest argumentem odwołania. Jest to przeznaczone dla argumentów metody.

`FIELD_MOD_HIDDEN`\
Wskazuje, że pole musi być ukryte lub zaprezentowane w innym kontekście; na przykład [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statyczne zmienne lokalne.

`FIELD_MOD_MARSHALASOBJECT`\
Wskazuje, że pole reprezentuje obiekt z `IUnknown` interfejsem.

`FIELD_MOD_SPECIAL_NAME`\
Wskazuje, że pole ma specjalną nazwę, na przykład `.ctor` dla konstruktora ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] tylko).

`FIELD_MOD_HIDEBYSIG`\
Wskazuje, że do pola jest `Overloads` stosowane słowo kluczowe ( [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] tylko).

`FIELD_MOD_WRITEONLY`\
Wskazuje, że pole jest tylko do zapisu. Ta wartość nie jest uwzględniona w `FIELD_MOD_ALL` , ponieważ jedynym zastosowaniem pól tylko do zapisu jest obliczanie funkcji. Użytkownik musi jawnie zażądać `FIELD_MOD_WRITEONLY` pól.

`FIELD_MOD_ACCESS_MASK`\
Wskazuje maskę dostępu do pola.

`FIELD_MOD_MASK`\
Wskazuje maskę dla modyfikatorów pól.

## <a name="remarks"></a>Uwagi
Używane dla `dwModifiers` elementu członkowskiego struktury [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

Te wartości są również przesyłane do metody [EnumFields —](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) w celu filtrowania określonych pól.

## <a name="requirements"></a>Wymagania
Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
