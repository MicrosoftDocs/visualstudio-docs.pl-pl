---
title: DEBUG_PROPERTY_INFO | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7804cfad48d5029e16619b5ae524fa6e761f11b4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346182"
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
Zawiera informacje dotyczące właściwości debugowania.

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
Kombinacja flag z [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) wyliczenia, która określa, które pola są wypełniane.

`bstrFullName`\
Pełna nazwa właściwości.

`bstrName`\
Nazwa właściwości w kontekście.

`bstrType`\
Typ właściwości jako ciąg formatowania.

`bstrValue`\
Wartość właściwości jako ciąg formatowania.

`pProperty`\
[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektem opisanym przez tę strukturę.

`dwAttrib`\
Kombinacja flag z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) wyliczenie opisujące atrybuty tej właściwości.

## <a name="remarks"></a>Uwagi
Właściwość jest obiekt hierarchiczny charakter, który ma nazwę, typ i wartość. Na przykład właściwość można opisać zmiennych lokalnych, parametrów, Czujka, zmienne i wyrażenia i rejestrów.

Ta struktura jest przekazywany do [getpropertyinfo —](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody, gdzie jest wypełnione. Ta struktura jest także zwracany jako część listy tej struktury z [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) interfejs, który z kolei jest zwracany z wywołania [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) i [ Enumproperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
