---
description: Ta struktura opisuje zmienną lokalną, parametr lub inne pole.
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27055178f01f41bb6b4642b8c4d70ea6346b9e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059426"
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
Kombinacja flag z wyliczenia [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) , która określa, które elementy członkowskie są wypełnione.

`bstrFullName`\
Pełna nazwa pola.

`bstrName`\
Krótka nazwa pola.

`bstrType`\
Typ pola.

`dwModifiers`\
Kombinacja flag z wyliczenia [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) , który opisuje pole.

## <a name="remarks"></a>Uwagi
Ta struktura jest przenoszona do metody [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) , w której jest wypełniana.

## <a name="requirements"></a>Wymagania
Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
