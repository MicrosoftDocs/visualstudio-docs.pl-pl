---
title: 'IDebugStackFrame:: GetLanguageString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83abb038cd8bc018d84cd0c5ddd2a413f8a02248
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576757"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Zwraca krótki lub długi tekstowy opis języka.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 podczas Flaga, gdzie `TRUE` zwraca długi opis i `FALSE` zwraca Krótki opis.  
  
 `pbstrLanguage`  
 określoną Opis języka.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj jeśli `fLong` jest `FALSE`, ta metoda zawiera tylko nazwę języka skojarzonego z ramką stosu. Gdy `fLong` jest `TRUE`, ta metoda może dostarczyć pełny opis produktu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugStackFrame, interfejs](../../winscript/reference/idebugstackframe-interface.md)