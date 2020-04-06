---
title: DEBUGREF_INFO_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737389"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Określa, jakie informacje mają być pobierane o obiekcie odwołania do debugowania.

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
Inicjowanie/używanie `bstrName` pola w strukturze.

`DEBUGREF_INFO_TYPE`\
Inicjowanie/używanie `bstrType` pola w strukturze.

`DEBUGREF_INFO_VALUE`\
Inicjowanie/używanie `bstrValue` pola w strukturze.

`DEBUGREF_INFO_ATTRIB`\
Inicjowanie/używanie `dwAttrib` pola w strukturze.

`DEBUGREF_INFO_REFTYPE`\
Inicjowanie/używanie `dwRefType` pola w strukturze.

`DEBUGREF_INFO_REF`\
Inicjowanie/używanie `pReference` pola w strukturze.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Pole wartości powinno zawierać automatycznie rozwiniętą wartość dla tego typu obiektu, jeśli jest dostępna.

`DEBUGREF_INFO_NONE`\
Wskazuje, że nie ustawiono żadnych flag.

`DEBUGREF_INFO_ALL`\
Wskazuje maskę flag.

## <a name="remarks"></a>Uwagi
Flagi te są przekazywane do [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) i [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metody, aby wskazać, które pola [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury mają zostać zainicjowane.

Używane dla `dwFields` elementu `DEBUG_REFERENCE_INFO` członkowskiego struktury, aby wskazać, które pola są używane i prawidłowe, gdy struktura jest zwracana.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
