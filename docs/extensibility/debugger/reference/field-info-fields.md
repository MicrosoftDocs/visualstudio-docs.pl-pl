---
description: Określa informacje do pobrania dotyczące obiektu IDebugField.
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
ms.openlocfilehash: 024c12d5112398e055141a8db4995f2801ca5401
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170292"
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
