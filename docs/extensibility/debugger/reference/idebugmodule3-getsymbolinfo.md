---
description: Pobiera listę ścieżek przeszukiwanych pod kątem symboli, a także wyniki wyszukiwania każdej ścieżki.
title: 'IDebugModule3:: GetSymbolInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9cc4c8d7c88e4b973ad7055327da73472a6ed4d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065531"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Pobiera listę ścieżek przeszukiwanych pod kątem symboli, a także wyniki wyszukiwania każdej ścieżki.

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
podczas Kombinacja flag z wyliczenia [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) określająca, które pola `pInfo` mają być wypełnione.

`pInfo`\
określoną Struktura [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) , której członkowie są wypełniani określonymi informacjami. Jeśli jest to wartość null, ta metoda zwraca `E_INVALIDARG` .

## <a name="return-value"></a>Wartość zwracana
Jeśli metoda się powiedzie, zwraca wartość `S_OK` ; w przeciwnym razie zwraca kod błędu.

> [!NOTE]
> Zwrócony ciąg (w `MODULE_SYMBOL_SEARCH_INFO` strukturze) może być pusty nawet wtedy, gdy `S_OK` jest zwracany. W takim przypadku nie ma informacji o przeszukiwaniu do zwrócenia.

## <a name="remarks"></a>Uwagi
Jeśli `bstrVerboseSearchInfo` pole `MODULE_SYMBOL_SEARCH_INFO` struktury nie jest puste, zawiera listę przeszukanych ścieżek oraz wyniki tego wyszukiwania. Lista jest formatowana ze ścieżką, po której następuje wielokropek ("..."), a następnie wynik. Jeśli istnieje więcej niż jedna para wyników ścieżki, każda para jest oddzielona przez parę "\r\n" (karetka-Return/wysuwu wiersza). Wzorzec wygląda następująco:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Należy zauważyć, że ostatni wpis nie ma sekwencji \r\n.

## <a name="example"></a>Przykład
W tym przykładzie metoda zwraca trzy ścieżki z trzema różnymi wynikami wyszukiwania. Każdy wiersz jest zakończony przez parę karetki/wysuwu wiersza. Przykładowe dane wyjściowe po prostu drukują wyniki wyszukiwania jako jeden ciąg.

> [!NOTE]
> Wynik stanu to wszystko bezpośrednio po "..." do końca wiersza.

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

**c:\symbols\user32.pdb... Nie znaleziono pliku.** 
 **c:\winnt\symbols\user32.pdb... Wersja nie jest zgodna.** 
 **\\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... Załadowano symbole.**

## <a name="see-also"></a>Zobacz też

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
