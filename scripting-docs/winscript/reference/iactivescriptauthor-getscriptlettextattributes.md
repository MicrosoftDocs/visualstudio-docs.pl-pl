---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8f1b5aac6df8d8659fa323f3f1efcb7721d97f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955062"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Zwraca atrybuty tekstu scriptlet.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [w size_is (`cch`)] tekstu scriptlet. Ten ciąg ma być zakończone znakiem null.  
  
 `cch`  
 [in] Rozmiar umożliwiający `pszCode` i `pattr` parametrów.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika końcowego scriptlet. Gdy `pszCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika (takie jak dwa pojedyncze cudzysłowy), na aby wykrywać koniec scriptletu. Ustaw ten parametr na wartość NULL, jeśli nie było ogranicznika używany do identyfikowania końca scriptlet.  
  
 `dwFlags`  
 [in] Flagi, które są skojarzone z atrybutów tekstu Scriptlet. Może być kombinacją następujących wartości.  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Określenie identyfikatorów, które mają atrybut SOURCETEXT_ATTR_IDENTIFIER i zidentyfikować kropka operatorów, które mają atrybut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Zidentyfikuj bieżącego obiektu, który ma atrybut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Zidentyfikuj tekst zawartości i komentarz ciąg, który ma atrybut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [w poziomie, size_is (`cch`)] informacji o kolorze do kodu scriptlet.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)