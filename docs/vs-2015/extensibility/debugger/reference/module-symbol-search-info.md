---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2cfbaf8c3756bf758956d1f1e5964d8e9f8f0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205182"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zawiera informacje o stanie dotyczące przeszukanych ścieżek wyszukiwania symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `dwValidFields`  
 Kombinacja flag z wyliczenia [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) , określając rodzaj informacji wyszukiwania opisanych w tej strukturze.  
  
 `bstrVerboseSearchInfo`  
 Ścieżka wyszukiwania i wyniki są łączone w jeden ciąg.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracana z wywołania metody [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .  
  
 Jeśli `bstrVerboseSearchInfo` pole nie jest puste, zawiera listę przeszukanych ścieżek i wyniki tego wyszukiwania. Lista jest formatowana ze ścieżką, po której następuje Elipsa ("..."), po której następuje wynik. Jeśli istnieje więcej niż jedna para wyników ścieżki, każda para jest oddzielona przez parę "\r\n" (karetka-Return/wysuwu wiersza). Wzorzec wygląda następująco:  
  
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
 [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
