---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 131e014e3714df708c5ef1526ecb911531c5a5c3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689112"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Określa, jakie informacje należy pobrać o obiekcie właściwości debugowania.

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

## <a name="members"></a>Elementy członkowskie
DEBUGPROP_INFO_FULLNAME zainicjować bądź użyj `bstrFullName` pola.

DEBUGPROP_INFO_NAME zainicjować bądź użyj `bstrName` pola.

DEBUGPROP_INFO_TYPE zainicjować bądź użyj `bstrType` pola.

DEBUGPROP_INFO_VALUE zainicjować bądź użyj `bstrValue` pola.

DEBUGPROP_INFO_ATTRIB zainicjować bądź użyj `dwAttrib` pola.

DEBUGPROP_INFO_PROP zainicjować bądź użyj `pProperty` pola, które zawiera [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.

DEBUGPROP_INFO_VALUE_AUTOEXPAND oznacza, że wartość pola może zawierać wartość rozwinięte automatycznie, jeśli są dostępne dla tego typu obiektu.

DEBUGPROP_INFO_VALUE_NOFUNCEVAL Deprecated.

DEBUGPROP_INFO_VALUE_RAW nie zwracają żadnych wartości beautified lub elementów członkowskich (czyli nie Formatuj wartości).

DEBUGPROP_INFO_VALUE_NO_TOSTRING nie zwracają żadnych specjalnych wartości syntetyzowany (na przykład nie należy wywoływać metody `ToString()` na obiekcie w celu utworzenia wartości).

DEBUGPROP_INFO_NONE Określa, że ustawiono bez flag.

DEBUGPROP_INFO_STANDARD zainicjować bądź użyj `dwAttrib`, `bstrName`, `bstrType`, i `bstrValue` pola.

DEBUGPROP_INFO_All wskazuje maskę wszystkie flagi.

## <a name="remarks"></a>Uwagi
Te wartości są przekazywane do [getpropertyinfo —](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), i [enumproperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metod, aby określić pola, które mają zostać zainicjowane [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.

Te wartości są używane również do `dwFields` członkiem `DEBUG_PROPERTY_INFO` struktury, aby wskazać, pola, które struktury są używane i ważne, gdy zwracany jest struktura.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
