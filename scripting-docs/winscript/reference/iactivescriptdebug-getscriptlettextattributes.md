---
title: 'IActiveScriptDebug:: GetScriptletTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a5dd9e219e51b001659225636396fe45ac815b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572811"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Zwraca atrybuty tekstu dla dowolnych Scriptlet.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 podczas Tekst Scriptlet. Ten ciąg nie może być zakończony znakiem null.  
  
 `uNumCodeChars`  
 podczas Liczba znaków w tekście Scriptlet.  
  
 `pstrDelimiter`  
 podczas Adres ogranicznika końca Scriptlet. Gdy `pstrCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika, takiego jak dwa znaki pojedynczego cudzysłowu (' '), aby wykryć koniec Scriptlet. Ten parametr określa ogranicznik używany przez hosta, który umożliwia aparatowi obsługi skryptów dostarczenie pewnych warunkowego przetwarzania wstępnego (na przykład zastępowanie pojedynczego cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użycia jako ogranicznika). Dokładnie tak, jak (i jeśli) aparat skryptów używa tych informacji, zależy od aparatu skryptów. Ustaw ten parametr na wartość NULL, Jeśli host nie używał ogranicznika do oznaczenia końca Scriptlet.  
  
 `dwFlags`  
 podczas Flagi skojarzone z Scriptlet. Może być kombinacją następujących wartości:  
  
|Stała|Value|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Wskazuje, że identyfikatory i operatory kropek powinny być identyfikowane odpowiednio flagami SOURCETEXT_ATTR_IDENTIFIER i SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Wskazuje, że identyfikator dla bieżącego obiektu powinien być zidentyfikowany przy użyciu flagi SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Wskazuje, że zawartość ciągu i tekst komentarza powinny być identyfikowane za pomocą flagi SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in. out] Bufor zawierający zwrócone atrybuty.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Inteligentny host implementujący interfejs `IDebugDocumentText` może używać tej metody do delegowania wywołań do metody `IDebugDocumentText::GetText`.  
  
 To wywołanie jest dostarczone, ponieważ skryptlety ma być wyrażeniami i może mieć inną składnię niż blok skryptu. Jeśli mają tę samą składnię, implementacja tej metody będzie taka sama jak implementacja metody `GetScriptTextAttributes`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptDebug  interfejsu](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText  interfejsu](../../winscript/reference/idebugdocumenttext-interface.md)  
 [IDebugDocumentText:: gettext](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)