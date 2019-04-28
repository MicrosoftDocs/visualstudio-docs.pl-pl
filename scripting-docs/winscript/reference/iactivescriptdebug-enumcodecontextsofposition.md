---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c364d00941a65272b4d22cc7674a0f0e6178f099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009745"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Używany przez hosta inteligentnego, aby delegować `IDebugDocumentContext::EnumCodeContexts` metody.  
  
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
 [in] Kontekst źródła udostępnionych `IActiveScriptParse::ParseScriptText` lub `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Znak przesunięcie względem początku tekst skryptu.  
  
 `uNumChars`  
 [in] Liczba znaków w tym kontekście.  
  
 `ppescc`  
 [out] Moduł wyliczający kontekstów kodu w określonym zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Hostów inteligentnych ta metoda umożliwia delegowanie `IDebugDocumentContext::EnumCodeContexts` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)