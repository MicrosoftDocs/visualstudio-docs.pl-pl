---
title: 'IActiveScriptAuthor:: GetScriptTextAttributes | Microsoft Docs'
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
ms.openlocfilehash: f89c7b654cc2ac7248598ee6498a3a290d17e2ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72563151"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Zwraca atrybuty tekstu bloku skryptu.  
  
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
 [in, size_is (`cch`)] Tekst bloku skryptu. Ten ciąg nie musi być zakończony znakiem null.  
  
 `cch`  
 podczas Rozmiar używany dla parametrów `pszCode` i `pattr`.  
  
 `pszDelimiter`  
 podczas Adres ogranicznika końca skryptu. Gdy `pszCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika (takiego jak dwa znaki pojedynczego cudzysłowu) w celu wykrycia końca Scriptlet. Ustaw ten parametr na wartość NULL, jeśli nie ma ogranicznika identyfikującego koniec bloku skryptu.  
  
 `dwFlags`  
 podczas Flagi, które są skojarzone z atrybutami tekstu bloku skryptu. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Zidentyfikuj identyfikatory, które mają atrybut SOURCETEXT_ATTR_IDENTIFIER i Identyfikuj operatory punktów, które mają atrybut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Zidentyfikuj bieżący obiekt, który ma atrybut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Zidentyfikuj zawartość ciągu i tekst komentarza, który ma atrybut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Informacje o kolorze dla kodu bloku skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthor   interfejsu](../../winscript/reference/iactivescriptauthor-interface.md)  
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)