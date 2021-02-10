---
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e491054ffbdfa9e19cb8bed995b2f369ac1a885
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939178"
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
Kombinacja flag z wyliczenia [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , która określa, które pola są wypełniane.

`bstrName`\
Określona przez użytkownika nazwa obiektu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

`bstrType`\
Typ referencyjny jako sformatowany ciąg.

`bstrValue`\
Wartość odwołania jako sformatowany ciąg

`dwAttrib`\
Kombinacja flag z wyliczenia [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , która określa flagi dla atrybutów właściwości debugowania.

`dwRefType`\
Wartość z wyliczenia [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) , która określa, czy typ odwołania jest silny, czy słaby.

`m_pReference`\
Obiekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , który określa informacje referencyjne.

## <a name="remarks"></a>Uwagi
Ta struktura jest przenoszona do wywołania metody [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) w celu wypełnienia. Ta struktura jest również zwracana jako część listy z interfejsu [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) , który z kolei jest zwracany przez wywołanie metody [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

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
