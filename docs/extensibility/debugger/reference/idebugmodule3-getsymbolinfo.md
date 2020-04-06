---
title: IDebugModule3::GetSymbolInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726892"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Pobiera listę ścieżek, które są wyszukiwane symbole, a także wyniki wyszukiwania każdej ścieżki.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[w] Kombinacja flag z wyliczenia [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) określająca, `pInfo` które pola mają być wypełnione.

`pInfo`\
[na zewnątrz] Struktura [MODULE_SYMBOL_SEARCH_INFO,](../../../extensibility/debugger/reference/module-symbol-search-info.md) której elementy członkowskie mają być wypełnione określonymi informacjami. Jeśli jest to wartość null, `E_INVALIDARG`ta metoda zwraca .

## <a name="return-value"></a>Wartość zwracana
Jeśli metoda powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Zwracany ciąg (w `MODULE_SYMBOL_SEARCH_INFO` strukturze) może `S_OK` być pusty, nawet jeśli jest zwracany. W takim przypadku nie było informacji o wyszukiwaniu do powrotu.

## <a name="remarks"></a>Uwagi
Jeśli `bstrVerboseSearchInfo` pole `MODULE_SYMBOL_SEARCH_INFO` struktury nie jest puste, zawiera listę przeszukiwanych ścieżek i wyniki tego wyszukiwania. Lista jest sformatowana ze ścieżką, po której następuje wielokropek ("..."), po którym następuje wynik. Jeśli istnieje więcej niż jedna para wyników ścieżki, każda para jest oddzielona parą "\r\n" (carriage-return/linefeed). Wzór wygląda następująco:

\<ścieżka>... \<> ścieżki>\r\n...\< \<> ścieżki>\r\n...\< \<> wynik

Należy zauważyć, że ostatni wpis nie ma sekwencji \r\n.

## <a name="example"></a>Przykład
W tym przykładzie ta metoda zwraca trzy ścieżki z trzech różnych wyników wyszukiwania. Każdy wiersz jest zakończony parą powrotu/wysuwu wiersza. Przykładowe dane wyjściowe po prostu drukuje wyniki wyszukiwania jako pojedynczy ciąg.

> [!NOTE]
> Wynik stanu jest wszystko bezpośrednio po "..." aż do końca linii.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\symbole\user32.pdb... Nie znaleziono pliku.** 
 **c:\winnt\symbols\user32.pdb... Wersja nie jest zgodna.** 
 ** \\\symbole\symbole\user32.dll\0a8sd0ad8ad\user32.pdb... Załadowane symbole.**

## <a name="see-also"></a>Zobacz też

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
