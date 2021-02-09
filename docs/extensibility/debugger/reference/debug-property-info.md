---
title: DEBUG_PROPERTY_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98cd4292692fe9d9b965790ce9a0a30d55423454
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899092"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Zawiera informacje o właściwości debugowania.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Elementy członkowskie
`dwValidFields`\
Kombinacja flag z wyliczenia [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , która określa, które pola są wypełnione.

`bstrFullName`\
Pełna nazwa właściwości.

`bstrName`\
Nazwa właściwości w kontekście.

`bstrType`\
Typ właściwości jako sformatowany ciąg.

`bstrValue`\
Wartość właściwości jako sformatowany ciąg.

`pProperty`\
Obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) opisany przez tę strukturę.

`dwAttrib`\
Kombinacja flag z wyliczenia [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) opisującego atrybuty tej właściwości.

## <a name="remarks"></a>Uwagi
Właściwość jest obiektem o charakterze hierarchicznym, który ma nazwę, typ i wartość. Na przykład właściwość może opisywać zmienne lokalne, parametry, obserwacje zmiennych i wyrażeń oraz rejestrów.

Ta struktura jest przenoszona do metody [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) , gdzie jest wypełniona. Ta struktura jest również zwracana jako część listy tej struktury z interfejsu [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , który z kolei jest zwracany z wywołania metod [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) i [EnumProperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
