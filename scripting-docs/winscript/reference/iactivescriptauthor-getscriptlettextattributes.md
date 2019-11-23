---
title: 'IActiveScriptAuthor:: GetScriptletTextAttributes | Microsoft Docs'
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
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576167"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Zwraca atrybuty tekstu Scriptlet.  
  
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
 [in, size_is (`cch`)] Tekst Scriptlet. Ten ciąg nie musi być zakończony znakiem null.  
  
 `cch`  
 podczas Rozmiar używany dla parametrów `pszCode` i `pattr`.  
  
 `pszDelimiter`  
 podczas Adres ogranicznika końca Scriptlet. Gdy `pszCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika (takiego jak dwa znaki pojedynczego cudzysłowu) w celu wykrycia końca Scriptlet. Ustaw dla tego parametru wartość NULL, jeśli nie jest używany ogranicznik do identyfikowania końca Scriptlet.  
  
 `dwFlags`  
 podczas Flagi, które są skojarzone z atrybutami tekstu Scriptlet. Może być kombinacją następujących wartości.  
  
|Stała|Value|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Zidentyfikuj identyfikatory, które mają atrybut SOURCETEXT_ATTR_IDENTIFIER i Identyfikuj operatory punktów, które mają atrybut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Zidentyfikuj bieżący obiekt, który ma atrybut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Zidentyfikuj zawartość ciągu i tekst komentarza, który ma atrybut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in. out, size_is (`cch`)] Informacje o kolorze dla kodu Scriptlet.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor  interfejsu](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)