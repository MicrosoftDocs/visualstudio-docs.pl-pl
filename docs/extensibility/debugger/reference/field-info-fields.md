---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01853df78bfe731ea4b7159f7b3ebe352f3c5eaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337670"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Określa, jakie informacje należy pobrać o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.

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
Inicjowanie bądź użyj `bstrFullName` pole [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.

`FIF_NAME`\
Inicjowanie bądź użyj `bstrName` pole `FIELD_INFO` struktury.

`FIF_TYPE`\
Inicjowanie bądź użyj `bstrType` pole `FIELD_INFO` struktury.

`FIF_MODIFIERS`\
Inicjowanie bądź użyj `bstrModifiers` pole `FIELD_INFO` struktury.

## <a name="remarks"></a>Uwagi
Te wartości również są przekazywane jako argument do [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodę, aby określić które pola [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury, które mają zostać zainicjowane.

Te wartości są również używane w `dwFields` członkiem `FIELD_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.

Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: sh.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
