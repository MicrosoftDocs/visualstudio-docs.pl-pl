---
description: Określa, jakie informacje mają być pobierane na temat obiektu odwołania debugowania.
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913490588fcf739e9659318cb72a9ca74d6db99d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096229"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Określa, jakie informacje mają być pobierane na temat obiektu odwołania debugowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Pola
`DEBUGREF_INFO_NAME`\
Zainicjuj/Użyj `bstrName` pola w strukturze.

`DEBUGREF_INFO_TYPE`\
Zainicjuj/Użyj `bstrType` pola w strukturze.

`DEBUGREF_INFO_VALUE`\
Zainicjuj/Użyj `bstrValue` pola w strukturze.

`DEBUGREF_INFO_ATTRIB`\
Zainicjuj/Użyj `dwAttrib` pola w strukturze.

`DEBUGREF_INFO_REFTYPE`\
Zainicjuj/Użyj `dwRefType` pola w strukturze.

`DEBUGREF_INFO_REF`\
Zainicjuj/Użyj `pReference` pola w strukturze.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Pole Value powinno zawierać wartość autoexpanded (jeśli jest dostępna) dla tego typu obiektu.

`DEBUGREF_INFO_NONE`\
Wskazuje, że flagi nie są ustawione.

`DEBUGREF_INFO_ALL`\
Wskazuje maskę flag.

## <a name="remarks"></a>Uwagi
Te flagi są przesyłane do metod [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) i [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) , aby wskazać, które pola struktury [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) mają być inicjowane.

Używane dla `dwFields` składowej struktury, `DEBUG_REFERENCE_INFO` Aby wskazać, które pola są używane i są ważne podczas zwracania struktury.

Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
