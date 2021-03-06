---
description: Zawiera informacje o stanie dotyczące przeszukanych ścieżek wyszukiwania symboli.
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc914334fc4b8ebf2dd73f691cdec242e19364a9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222292"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Zawiera informacje o stanie dotyczące przeszukanych ścieżek wyszukiwania symboli.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Elementy członkowskie

`dwValidFields`\
Kombinacja flag z wyliczenia [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) , określając rodzaj informacji wyszukiwania opisanych w tej strukturze.

`bstrVerboseSearchInfo`\
Ścieżka wyszukiwania i wyniki są łączone w jeden ciąg.

## <a name="remarks"></a>Uwagi

Ta struktura jest zwracana z wywołania metody [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .

Jeśli `bstrVerboseSearchInfo` pole nie jest puste, zawiera listę przeszukanych ścieżek i wyniki tego wyszukiwania. Lista jest formatowana ze ścieżką, po której następuje wielokropek ("..."), a następnie wynik. Jeśli istnieje więcej niż jedna para wyników ścieżki, każda para jest oddzielona przez parę "\r\n" (karetka-Return/wysuwu wiersza). Wzorzec wygląda następująco:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Należy zauważyć, że ostatni wpis nie ma sekwencji \r\n.

Oto możliwy `bstrVerboseSearchInfo` ciąg, który został wysłany do warstwy Standardowa.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Wymagania

Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
