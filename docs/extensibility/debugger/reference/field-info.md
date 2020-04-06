---
title: FIELD_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736893"
---
# <a name="field_info"></a>FIELD_INFO
Ta struktura opisuje zmienną lokalną, parametr lub inne pole.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Elementy członkowskie
`dwFields`\
Kombinacja flag z wyliczenia [FIELD_INFO_FIELDS,](../../../extensibility/debugger/reference/field-info-fields.md) która określa, które elementy członkowskie są wypełniane.

`bstrFullName`\
Pełna nazwa pola.

`bstrName`\
Krótka nazwa pola.

`bstrType`\
Typ pola.

`dwModifiers`\
Kombinacja flag z wyliczenia [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) opisujące pole.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywana do [Metody GetInfo,](../../../extensibility/debugger/reference/idebugfield-getinfo.md) gdzie jest wypełniona.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
