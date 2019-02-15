---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b34624672b64d88ca9b080094c5d661494c089cf
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315901"
---
# <a name="fieldinfo"></a>FIELD_INFO
Ta struktura zawiera opis zmiennej lokalnej, parametr lub innego pola.

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
dwFields  
Kombinacja flag z [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) wyliczenie, które określa, które elementy członkowskie są wypełniane.

bstrFullName  
Pełna nazwa pola.

bstrName  
Krótka nazwa pola.

bstrType  
Typ pola.

dwModifiers  
Kombinacja flag z [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) wyliczenie opisujące pola.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywany do [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metody, gdzie jest wypełnione.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)  
[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)  
[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
