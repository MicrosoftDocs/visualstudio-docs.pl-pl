---
title: 'IActiveScriptDebug:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576929"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Zwraca atrybuty tekstu dla dowolnego bloku tekstu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 podczas Tekst bloku skryptu. Ten ciąg nie może być zakończony znakiem null.  
  
 `uNumCodeChars`  
 podczas Liczba znaków w tekście bloku skryptu.  
  
 `pstrDelimiter`  
 podczas Adres ogranicznika bloku końca skryptu. Gdy `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), w celu wykrycia końca bloku skryptu. Ten parametr określa ogranicznik używany przez hosta, który umożliwia aparatowi obsługi skryptów dostarczenie pewnych warunkowego przetwarzania wstępnego (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr na wartość NULL, Jeśli host nie używał ogranicznika do oznaczenia końca bloku skryptu.  
  
 `dwFlags`  
 podczas Flagi skojarzone z blokiem skryptu. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Wskazuje, że identyfikatory i operatory kropek powinny być identyfikowane odpowiednio flagami SOURCETEXT_ATTR_IDENTIFIER i SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Wskazuje, że identyfikator dla bieżącego obiektu powinien być zidentyfikowany przy użyciu flagi SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Wskazuje, że zawartość ciągu i tekst komentarza powinny być identyfikowane przy użyciu flagi SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in. out] Bufor zawierający zwrócone atrybuty.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Inteligentny host implementujący interfejs `IDebugDocumentText` może używać tej metody do delegowania wywołań do metody `IDebugDocumentText::GetText`.  
  
 Ta metoda dla bloków skryptu; Metoda `GetScriptletTextAttributes` jest dla skryptlety.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptDebug   interfejsu](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IActiveScriptDebug:: GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)    
 [IDebugDocumentText   interfejsu](../../winscript/reference/idebugdocumenttext-interface.md)  
 [IDebugDocumentText:: gettext](../../winscript/reference/idebugdocumenttext-gettext.md)    
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)