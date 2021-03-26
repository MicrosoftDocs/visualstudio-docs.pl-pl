---
description: Określa, jakie informacje mają być pobierane względem obiektu właściwości debugowania.
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84e52867c44fa1387aaf7501a827168651099e9c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096216"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Określa, jakie informacje mają być pobierane względem obiektu właściwości debugowania.

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
Zainicjuj/Użyj `bstrFullName` pola.

`DEBUGPROP_INFO_NAME`\
Zainicjuj/Użyj `bstrName` pola.

`DEBUGPROP_INFO_TYPE`\
Zainicjuj/Użyj `bstrType` pola.

`DEBUGPROP_INFO_VALUE`\
Zainicjuj/Użyj `bstrValue` pola.

`DEBUGPROP_INFO_ATTRIB`\
Zainicjuj/Użyj `dwAttrib` pola.

`DEBUGPROP_INFO_PROP`\
Zainicjuj/Użyj `pProperty` pola, które zawiera interfejs [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Określa, że pole wartości powinno zawierać wartość autoexpanded (jeśli jest dostępna) dla tego typu obiektu.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Przestarzałe.

`DEBUGPROP_INFO_VALUE_RAW`\
Nie zwracają żadnych wartości beautified ani elementów członkowskich (oznacza to, że wartości nie są formatowane).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Nie zwracają żadnych specjalnych wartości z syntezą (na przykład nie wywołuj obiektu, `ToString()` Aby utworzyć wartość).

`DEBUGPROP_INFO_NONE`\
Określa, że flagi nie są ustawione.

`DEBUGPROP_INFO_STANDARD`\
Inicjuj/używaj `dwAttrib` pól, `bstrName` , `bstrType` i `bstrValue` .

`DEBUGPROP_INFO_All`\
Wskazuje maskę wszystkich flag.

## <a name="remarks"></a>Uwagi
Te wartości są przesyłane do metod [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)i [EnumProperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) , aby wskazać, które pola mają być inicjowane przez strukturę [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

Te wartości są również używane dla `dwFields` składowej struktury, `DEBUG_PROPERTY_INFO` Aby wskazać, które pola struktury są używane i są prawidłowe podczas zwracania struktury.

Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
