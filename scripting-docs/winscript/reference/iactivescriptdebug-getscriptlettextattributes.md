---
title: IActiveScriptDebug::GetScriptletTextAttributes | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 781282b5c825954ada4fbb35daa2a97b379c3f13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955045"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Zwraca atrybuty tekstu dla dowolnego scriptlet.  
  
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
 [in] Tekstu scriptlet. Ten ciąg nie muszą być zakończone znakiem null.  
  
 `uNumCodeChars`  
 [in] Liczba znaków w tekstu scriptlet.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznika końcowego scriptlet. Gdy `pstrCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika, takiego jak dwa pojedyncze cudzysłowy ("), aby wykrywać koniec scriptletu. Ten parametr określa ogranicznik używany przez hosta, dzięki czemu silnik wykonywania skryptów zapewnić pierwotne przetwarzanie warunkowe (na przykład, zastępując pojedynczy znak cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użytku w roli ogranicznika). Dokładnie jak (i czy) używa aparatu skryptów, te informacje zależy od silnika wykonywania skryptów. Ustaw ten parametr na wartość NULL, jeśli host nie korzystał z ogranicznika do oznaczenia końca scriptlet.  
  
 `dwFlags`  
 [in] Flagi skojarzone ze scriptlet. Może być kombinacją tych wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Wskazuje, że operatory kropka i identyfikatory powinny identyfikowany za pomocą flagi SOURCETEXT_ATTR_IDENTIFIER i SOURCETEXT_ATTR_MEMBERLOOKUP, odpowiednio.|  
|GETATTRFLAG_THIS|0x0100|Wskazuje, że identyfikator dla bieżącego obiektu powinny zostać określone z flagą SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Wskazuje, czy ciąg tekstu zawartości i komentarz powinny zostać określone z flagą SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [out w] Bufor do przechowywania atrybutów zwracane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta inteligentnego, który implementuje `IDebugDocumentText` interfejsu ta metoda umożliwia delegowanie wywołań `IDebugDocumentText::GetText` metody.  
  
 To wywołanie jest dostarczane, ponieważ skryptlety są wyrażenia, a także mogą mieć innej składni niż blok skryptu. Jeśli mają tę samą składnię, implementacja tej metody będzie taka sama jak implementacja `GetScriptTextAttributes` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)