---
title: FIELD_INFO_FIELDS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736909"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Określa, jakie informacje mają być pobierane o obiekcie [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Składnia

```cpp
enum enum_FIELD_INFO_FIELDS { 
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
Inicjuj/użyj `bstrFullName` pola w strukturze [FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Inicjowanie/używanie `bstrName` pola `FIELD_INFO` w strukturze.

`FIF_TYPE`\
Inicjowanie/używanie `bstrType` pola `FIELD_INFO` w strukturze.

`FIF_MODIFIERS`\
Inicjowanie/używanie `bstrModifiers` pola `FIELD_INFO` w strukturze.

## <a name="remarks"></a>Uwagi
Wartości te są również przekazywane jako argument do [Metody GetInfo,](../../../extensibility/debugger/reference/idebugfield-getinfo.md) aby określić, które pola [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury mają być inicjowane.

Wartości te są również `dwFields` używane `FIELD_INFO` w człończu struktury, aby wskazać, które pola są używane i prawidłowe.

Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
