---
title: 'IActiveScriptDebug:: EnumCodeContextsOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572782"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Używane przez inteligentnego hosta do delegowania metody `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 podczas Kontekst źródłowy podany do `IActiveScriptParse::ParseScriptText` lub `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 podczas Przesunięcie znaku względem początku tekstu skryptu.  
  
 `uNumChars`  
 podczas Liczba znaków w tym kontekście.  
  
 `ppescc`  
 określoną Moduł wyliczający kontekstów kodu w określonym zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Hosty inteligentne używają tej metody do delegowania metody `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptDebug   interfejsu](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)