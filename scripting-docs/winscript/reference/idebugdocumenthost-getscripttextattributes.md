---
title: IDebugDocumentHost::GetScriptTextAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 016073d2ce22ab814716efc204ce573ea17cd510
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092719"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Zwraca atrybuty tekst w bloku tekstu dokumentu.  
  
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
 [in] Tekst bloku skryptu. Ten ciąg nie musi być zakończony wartością null.  
  
 `uNumCodeChars`  
 [in] Liczba znaków w tekście bloku skryptu.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznika końcowego elementu skrypt bloku. Gdy `pstrCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika, takiego jak dwa pojedyncze cudzysłowy ("), aby wykrywać koniec bloku skryptu. Ten parametr określa ogranicznik używany przez hosta, dzięki czemu silnik wykonywania skryptów zapewnić pierwotne przetwarzanie warunkowe (na przykład, zastępując pojedynczy znak cudzysłowu ['] dwoma pojedynczymi cudzysłowami do użytku w roli ogranicznika). Dokładnie jak (i czy) używa aparatu skryptów, te informacje zależy od silnika wykonywania skryptów. Ustaw ten parametr na wartość NULL, jeśli host nie korzystał z ogranicznika do oznaczenia końca bloku skryptu.  
  
 `dwFlags`  
 [in] Flagi skojarzone z bloku skryptu. Może być kombinacją tych wartości:  
  
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
|`E_NOTIMPL`|Host używa tylko atrybutów domyślnych.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca atrybutów tekstu dla dowolnego bloku tekstu dokumentu. Dopuszcza dla hostów, aby zwrócić `E_NOTIMPL`, w którym to przypadku są używane atrybuty domyślne.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)