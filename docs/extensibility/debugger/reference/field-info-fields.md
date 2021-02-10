---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8cec892d65dc4e5d081063fa6b31def06fb7f85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936915"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Określa informacje do pobrania dotyczące obiektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Składnia

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Pola
`FIF_FULLNAME`\
Zainicjuj/Użyj `bstrFullName` pola w strukturze [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

`FIF_NAME`\
Zainicjuj/Użyj `bstrName` pola w `FIELD_INFO` strukturze.

`FIF_TYPE`\
Zainicjuj/Użyj `bstrType` pola w `FIELD_INFO` strukturze.

`FIF_MODIFIERS`\
Zainicjuj/Użyj `bstrModifiers` pola w `FIELD_INFO` strukturze.

## <a name="remarks"></a>Uwagi
Te wartości są również przekazywane jako argument do metody [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) , aby określić, które pola struktury [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) mają być inicjowane.

Te wartości są również używane w `dwFields` składowej struktury, `FIELD_INFO` Aby wskazać, które pola są używane i są prawidłowe.

Flagi te mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: sh. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
