---
title: DEBUG_REFERENCE_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737414"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Opisuje odwołanie.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Elementy członkowskie
`dwFields`\
Kombinacja flag z wyliczenia [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) określająca, które pola są wypełniane.

`bstrName`\
Nazwa określona przez użytkownika obiektu [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

`bstrType`\
Typ odwołania jako sformatowany ciąg.

`bstrValue`\
Wartość referencyjna jako sformatowany ciąg

`dwAttrib`\
Kombinacja flag z wyliczenia [DBG_ATTRIB_FLAGS,](../../../extensibility/debugger/reference/dbg-attrib-flags.md) która określa flagi atrybutów właściwości debugowania.

`dwRefType`\
Wartość z [wyliczenia REFERENCE_TYPE,](../../../extensibility/debugger/reference/reference-type.md) która określa, czy typ odwołania jest silny czy słaby.

`m_pReference`\
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekt, który określa informacje referencyjne.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywana do wywołania [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metody, które mają być wypełnione. Ta struktura jest również zwracana jako część listy z interfejsu [IEnumDebugReferenceInfo2,](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) który z kolei jest zwracany z wywołania do [Metody EnumChildren.](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
