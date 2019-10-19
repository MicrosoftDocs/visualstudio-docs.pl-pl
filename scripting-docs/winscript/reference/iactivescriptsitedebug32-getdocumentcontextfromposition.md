---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 7acbe2a5741fa94ac42470a85803d1720e0a8fa1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574847"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
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
 [IActiveScriptSiteDebug32, interfejs](../../winscript/reference/iactivescriptsitedebug32-interface.md)