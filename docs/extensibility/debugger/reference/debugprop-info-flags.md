---
title: DEBUGPROP_INFO_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737393"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Określa, jakie informacje mają być pobierane o obiekcie właściwości debugowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Pola
`DEBUGPROP_INFO_FULLNAME`\
Inicjowanie/używanie tego `bstrFullName` pola.

`DEBUGPROP_INFO_NAME`\
Inicjowanie/używanie tego `bstrName` pola.

`DEBUGPROP_INFO_TYPE`\
Inicjowanie/używanie tego `bstrType` pola.

`DEBUGPROP_INFO_VALUE`\
Inicjowanie/używanie tego `bstrValue` pola.

`DEBUGPROP_INFO_ATTRIB`\
Inicjowanie/używanie tego `dwAttrib` pola.

`DEBUGPROP_INFO_PROP`\
Inicjuj/użyj `pProperty` pola zawierającego interfejs [IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Określa, że pole wartości powinno zawierać wartość automatycznie rozwiniętą dla tego typu obiektu.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Przestarzałe.

`DEBUGPROP_INFO_VALUE_RAW`\
Nie zwracaj żadnych upiększonych wartości ani elementów członkowskich (czyli nie formatuj wartości).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Nie zwracaj żadnych specjalnych wartości syntetyzowanych `ToString()` (na przykład nie należy wywoływać obiektu w celu uzyskania wartości).

`DEBUGPROP_INFO_NONE`\
Określa, że nie ustawiono żadnych flag.

`DEBUGPROP_INFO_STANDARD`\
Inicjuj/użyj `bstrType`pól `bstrValue` `dwAttrib`, `bstrName`, i .

`DEBUGPROP_INFO_All`\
Wskazuje maskę wszystkich flag.

## <a name="remarks"></a>Uwagi
Wartości te są przekazywane do [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)i [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metody, aby wskazać, które pola mają być inicjowane [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.

Wartości te są również `dwFields` używane `DEBUG_PROPERTY_INFO` dla elementu członkowskiego struktury, aby wskazać, które pola struktury są używane i prawidłowe, gdy zwracana jest struktura.

Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
