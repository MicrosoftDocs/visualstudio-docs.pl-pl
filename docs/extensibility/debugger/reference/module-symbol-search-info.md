---
title: MODULE_SYMBOL_SEARCH_INFO | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714241"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Zawiera informacje o stanie przeszukiwanych ścieżek wyszukiwania symboli.

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
Kombinacja flag z wyliczenia [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) określająca rodzaj informacji wyszukiwania opisanych w tej strukturze.

`bstrVerboseSearchInfo`\
Ścieżka wyszukiwania i wyniki połączone w jeden ciąg.

## <a name="remarks"></a>Uwagi

Ta struktura jest zwracana z wywołania [getSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) metody.

Jeśli `bstrVerboseSearchInfo` pole nie jest puste, zawiera listę przeszukiwanych ścieżek i wyniki tego wyszukiwania. Lista jest sformatowana ze ścieżką, po której następuje wielokropek ("..."), po którym następuje wynik. Jeśli istnieje więcej niż jedna para wyników ścieżki, każda para jest oddzielona parą "\r\n" (carriage-return/linefeed). Wzór wygląda następująco:

\<ścieżka>... \<> ścieżki>\r\n...\< \<> ścieżki>\r\n...\< \<> wynik

Należy zauważyć, że ostatni wpis nie ma sekwencji \r\n.

Oto możliwy `bstrVerboseSearchInfo` ciąg, który został wysłany do standardu out.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Wymagania

Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
