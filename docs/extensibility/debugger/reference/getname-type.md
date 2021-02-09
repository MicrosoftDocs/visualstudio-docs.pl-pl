---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 541f8b51d4ce56b167abd3ecdb28d08bec0c02c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891270"
---
# <a name="getname_type"></a>GETNAME_TYPE
Określa typ nazwy plików do pobrania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Pola
`GN_NAME`\
Określa przyjazną nazwę dokumentu lub kontekstu.

`GN_FILENAME`\
Określa pełną ścieżkę do dokumentu lub kontekstu.

`GN_BASENAME`\
Określa nazwę pliku podstawowego zamiast pełnej ścieżki dokumentu lub kontekstu.

`GN_MONIKERNAME`\
Określa unikatową nazwę dokumentu lub kontekstu w formie monikera.

`GN_URL`\
Określa nazwę adresu URL dokumentu lub kontekstu.

`GN_TITLE`\
Określa tytuł dokumentu (jeśli taki istnieje).

`GN_STARTPAGEURL`\
Pobiera adres URL strony początkowej dla procesów.

## <a name="remarks"></a>Uwagi
Te wartości są przesyłane jako parametry do metod [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName i](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) , aby określić, jakiego rodzaju nazwa ma zostać zwrócona.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
