---
title: IDebugModule3::GetSymbolInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70dc54f8f3110fbfdccdaa9b9cd1be47396be45d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801833"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera listę ścieżek, które są przeszukiwane pod kątem symboli, a także wyniki wyszukiwania poszczególnych ścieżek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinacja flag z [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) wyliczenie opisujące który pola `pInfo` mają być wypełnione.  
  
 `pInfo`  
 [out] A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) strukturę, której członkami są w celu wprowadzenia określone informacje. Jeśli to jest wartość null, Metoda ta zwraca `E_INVALIDARG`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Zwracany ciąg (w `MODULE_SYMBOL_SEARCH_INFO` struktury) może być pusta nawet wtedy, gdy `S_OK` jest zwracana. W tym przypadku nie było żadnych informacji, aby zwrócić.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `bstrVerboseSearchInfo` pole `MODULE_SYMBOL_SEARCH_INFO` struktura nie jest pusty, a następnie zawiera listę ścieżek przeszukiwane i wyniki tego wyszukiwania. Lista jest formatowana ze ścieżką, w którym następuje wielokropek ("..."), a następnie wynik. W przypadku więcej niż jedną parę wynik ścieżki każdej pary jest oddzielony przez parę "\r\n" (powrót karetki return/wysuw wiersza). Wzorzec wygląda następująco:  
  
 \<Ścieżka >... \<wyniku > \r\n\<ścieżka >... \<wyniku > \r\n\<ścieżka >... \<wyniku >  
  
 Należy pamiętać, że ostatni wpis nie ma sekwencji \r\n.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie metoda ta zwraca trzy ścieżki na trzy inne wyniki wyszukiwania. Każdy wiersz jest kończony przy użyciu pary karetki return/wysuw wiersza. Przykładowe dane wyjściowe po prostu wyświetla wyniki wyszukiwania jako pojedynczy ciąg.  
  
> [!NOTE]
>  Wynik stanu to wszystko, co natychmiast po "..." do końca wiersza.  
  
```cpp#  
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
**c:\winnt\symbols\user32.pdb... Wersja jest niezgodna.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Załadowano symbole.**   
## <a name="see-also"></a>Zobacz też  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

