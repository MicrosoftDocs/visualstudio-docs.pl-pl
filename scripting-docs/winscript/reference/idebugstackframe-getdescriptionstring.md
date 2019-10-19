---
title: 'IDebugStackFrame:: GetDescriptionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7eb29574d240a02073721046cec65bdf483b3eb0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576743"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Zwraca krótki lub długi tekstowy opis ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 podczas Flaga, gdzie `TRUE` zwraca długi opis i `FALSE` zwraca Krótki opis.  
  
 `pbstrDescription`  
 określoną Opis ramki stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj jeśli `fLong` jest `FALSE`, ta metoda zawiera tylko nazwę funkcji skojarzonej z ramką stosu. Gdy `fLong` jest `TRUE`, ta metoda może także podawać parametry funkcji i inne istotne informacje.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugStackFrame, interfejs](../../winscript/reference/idebugstackframe-interface.md)