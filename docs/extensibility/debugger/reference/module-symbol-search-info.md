---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6886373e521c411c3823b9f15138c8f798a373f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913820"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO

Zawiera informacje o stanie dotyczące ścieżki wyszukiwania symboli, które zostały przeszukiwane.

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

## <a name="parameters"></a>Parametry

`dwValidFields`

Kombinacja flag z [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) wyliczenie opisujące rodzaju informacje o wyszukiwaniu opisane w tej strukturze.

`bstrVerboseSearchInfo`

Ścieżka wyszukiwania i wyników połączonych w jeden ciąg.

## <a name="remarks"></a>Uwagi

Ta struktura jest zwracany z wywołania [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) metody.

Jeśli `bstrVerboseSearchInfo` pole nie jest puste, a następnie zawiera listę ścieżek przeszukiwane i wyniki tego wyszukiwania. Lista jest formatowana ze ścieżką, w którym następuje wielokropek ("..."), a następnie wynik. W przypadku więcej niż jedną parę wynik ścieżki każdej pary jest oddzielony przez parę "\r\n" (powrót karetki return/wysuw wiersza). Wzorzec wygląda następująco:

\<path>...\<result>\r\n\<path>...\<result>\r\n\<path>...\<result>

Należy pamiętać, że ostatni wpis nie ma sekwencji \r\n.

Poniżej przedstawiono możliwe `bstrVerboseSearchInfo` ciąg, który została wysłana na standardowe wyjście.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Wymagania

Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także

- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)