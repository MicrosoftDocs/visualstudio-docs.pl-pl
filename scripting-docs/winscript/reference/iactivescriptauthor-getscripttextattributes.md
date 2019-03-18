---
title: IActiveScriptAuthor::GetScriptTextAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75e0d5edf7cf2f83e814036cec56a1b19a89813e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151937"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Zwraca atrybuty tekst w bloku skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [w size_is (`cch`)] tekst w bloku skryptu. Ten ciąg ma być zakończone znakiem null.  
  
 `cch`  
 [in] Rozmiar umożliwiający `pszCode` i `pattr` parametrów.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika końcowego elementu skryptu. Gdy `pszCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika (takie jak dwa pojedyncze cudzysłowy), na aby wykrywać koniec scriptletu. Ustaw ten parametr na wartość NULL, jeśli nie było ogranicznika do identyfikowania koniec bloku skryptu.  
  
 `dwFlags`  
 [in] Flagi, które są skojarzone z atrybutów tekstu w bloku skryptu. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Określenie identyfikatorów, które mają atrybut SOURCETEXT_ATTR_IDENTIFIER i zidentyfikować kropka operatorów, które mają atrybut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Zidentyfikuj bieżącego obiektu, który ma atrybut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Zidentyfikuj tekst zawartości i komentarz ciąg, który ma atrybut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [w poziomie, size_is (`cch`)] informacji o kolorze do kodu bloku skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)