---
title: 'IActiveScriptSiteDebug:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61bc36b98fee31ced1f3e8e00d084b5dabcd2124
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570173"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
Używane przez Aparat języka do delegowania `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 podczas Zawartość źródłowa zgodnie z `ParseScriptText` lub `AddScriptlet`.  
  
 `uCharacterOffset`  
 podczas Przesunięcie znaku względem początku bloku skryptu lub Scriptlet.  
  
 `uNumChars`  
 podczas Liczba znaków w tym kontekście.  
  
 `ppsc`  
 określoną Kontekst dokumentu odpowiadający zakresowi pozycji znaku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka używają tej metody do delegowania `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSiteDebug, interfejs](../../winscript/reference/iactivescriptsitedebug-interface.md)