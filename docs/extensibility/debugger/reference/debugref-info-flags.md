---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1adab87ed09ca2ff16d837da084d8cc0b76956fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318369"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Określa, jakie informacje należy pobrać o obiektu odwołania debugowania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Pola
`DEBUGREF_INFO_NAME`\
Inicjowanie bądź użyj `bstrName` pole w strukturze.

`DEBUGREF_INFO_TYPE`\
Inicjowanie bądź użyj `bstrType` pole w strukturze.

`DEBUGREF_INFO_VALUE`\
Inicjowanie bądź użyj `bstrValue` pole w strukturze.

`DEBUGREF_INFO_ATTRIB`\
Inicjowanie bądź użyj `dwAttrib` pole w strukturze.

`DEBUGREF_INFO_REFTYPE`\
Inicjowanie bądź użyj `dwRefType` pole w strukturze.

`DEBUGREF_INFO_REF`\
Inicjowanie bądź użyj `pReference` pole w strukturze.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Pole wartości powinien zawierać wartość rozwinięte automatycznie, jeśli są dostępne dla tego typu obiektu.

`DEBUGREF_INFO_NONE`\
Wskazuje, że nie flagi są ustawione.

`DEBUGREF_INFO_ALL`\
Określa maskę flag.

## <a name="remarks"></a>Uwagi
Te flagi są przekazywane do [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) i [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) metod, aby określić które pola [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury, które mają zostać zainicjowane.

Używany do `dwFields` członkiem `DEBUG_REFERENCE_INFO` struktury, aby wskazać, pola, które są używane i ważne, gdy zwracany jest struktura.

Te wartości mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
