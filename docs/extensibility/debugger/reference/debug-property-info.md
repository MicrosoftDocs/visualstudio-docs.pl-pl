---
title: DEBUG_PROPERTY_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737451"
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
Kombinacja flag z wyliczenia [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) określająca, które pola są wypełniane.

`bstrFullName`\
Pełna nazwa obiektu.

`bstrName`\
Nazwa właściwości w kontekście.

`bstrType`\
Typ właściwości jako sformatowany ciąg.

`bstrValue`\
Wartość właściwości jako sformatowany ciąg.

`pProperty`\
[Obiekt IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) opisany przez tę strukturę.

`dwAttrib`\
Kombinacja flag z wyliczenia [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) opisujące atrybuty tej właściwości.

## <a name="remarks"></a>Uwagi
Właściwość jest obiektem o charakterze hierarchicznym, który ma nazwę, typ i wartość. Na przykład właściwość może opisywać zmienne lokalne, parametry, obserwować zmienne i wyrażenia oraz rejestry.

Ta struktura jest przekazywana do [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody, gdzie jest wypełniona. Ta struktura jest również zwracana jako część listy tej struktury z interfejsu [IEnumDebugPropertyInfo2,](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) który z kolei jest zwracany z wywołania do [Metod Wyliczenia i](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) [EnumProperties.](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

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
