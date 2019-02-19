---
title: DEBUG_REFERENCE_INFO | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3167deaa7e088ed75584f9fdc0777a608f11a47e
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413478"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
W tym artykule opisano odwołania.

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
dwFields  
Kombinacja flag z [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) wyliczenia, która określa pola, które są wypełnione.

bstrName  
Określone przez użytkownika nazwa [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiektu.

bstrType  
Typ odwołania jako ciąg formatowania.

bstrValue  
Wartość odniesienia jako sformatowany ciąg

dwAttrib  
Kombinacja flag z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) wyliczenie, które określa flagi dla atrybutów właściwości debugowania.

dwRefType  
Wartość z zakresu od [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) wyliczenie, które określa, czy typ odwołania jest dobre lub słabe.

m_pReference  
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekt, który określa informacje odniesienia.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywany do wywołania [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metodę, aby wypełnić. Ta struktura jest także zwracany jako część listy z [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) interfejs, który z kolei jest zwracany z wywołania [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)  
[DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)  
[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)  
[REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)  
[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)  
[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)  
[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
