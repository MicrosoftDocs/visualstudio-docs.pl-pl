---
title: IDebugStackFrame::GetLanguageString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: cc20c3ce2f5d198e167b83ffddb65cedc84402d7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087740"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Zwraca krótki lub długo tekstowe Opis języka.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 [in] Flaga, gdzie `TRUE` zwraca długi opis i `FALSE` zwraca krótki opis.  
  
 `pbstrLanguage`  
 [out] Opis języka.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj Jeśli `fLong` jest `FALSE`, ta metoda zapewnia tylko nazwę języka skojarzone z ramki stosu. Gdy `fLong` jest `TRUE`, ta metoda może dostarczyć opis pełnej wersji produktu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame, interfejs](../../winscript/reference/idebugstackframe-interface.md)