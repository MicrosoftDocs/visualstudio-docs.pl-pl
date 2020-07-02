---
title: 'IActiveScriptSiteDebug32:: GetDocumentContextFromPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b43b16f46cc62b6c70460d79c194b5e0d2cfede0
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835280"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Używane przez Aparat języka do delegowania `IDebugCodeContext::GetSourceContext` .  
  
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
 podczas Zawartość źródłowa określona dla `ParseScriptText` lub `AddScriptlet` .  
  
 `uCharacterOffset`  
 podczas Przesunięcie znaku względem początku bloku skryptu lub Scriptlet.  
  
 `uNumChars`  
 podczas Liczba znaków w tym kontekście.  
  
 `ppsc`  
 określoną Kontekst dokumentu odpowiadający zakresowi pozycji znaku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT` . Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka używają tej metody do delegowania `IDebugCodeContext::GetSourceContext` .  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSiteDebug32, interfejs](../../winscript/reference/iactivescriptsitedebug32-interface.md)