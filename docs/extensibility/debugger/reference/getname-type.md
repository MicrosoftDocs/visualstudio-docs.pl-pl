---
title: GETNAME_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bdcbc4171c8a481ee0c45456ef5600f5150c6d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317584"
---
# <a name="getnametype"></a>GETNAME_TYPE
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
Określa pełną ścieżkę dokumentu lub kontekstu.

`GN_BASENAME`\
Określa nazwę pliku podstawowego zamiast pełnej ścieżki dokumentu lub kontekstu.

`GN_MONIKERNAME`\
Określa unikatową nazwę dokumentu lub kontekstu w postaci krótka.

`GN_URL`\
Określa nazwę adresu URL dokumentu lub kontekstu.

`GN_TITLE`\
Określa tytuł dokumentu, jeśli taka istnieje.

`GN_STARTPAGEURL`\
Pobiera początkowy adres URL strony dla procesów.

## <a name="remarks"></a>Uwagi
Te wartości są przekazywane jako parametry [getname —](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [getname —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), i [getname —](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metody, aby określić, jakiego rodzaju nazwy do zwrócenia.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
