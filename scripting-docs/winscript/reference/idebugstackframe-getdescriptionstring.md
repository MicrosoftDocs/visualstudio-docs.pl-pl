---
title: IDebugStackFrame::GetDescriptionString | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f870c6dbc654f8465d201c53443228153ce4a68b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934612"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Zwraca opis krótki lub długo tekstowych ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 [in] Flaga, gdzie `TRUE` zwraca długi opis i `FALSE` zwraca krótki opis.  
  
 `pbstrDescription`  
 [out] Opis ramki stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj Jeśli `fLong` jest `FALSE`, ta metoda zapewnia tylko nazwę funkcji, skojarzone z ramki stosu. Gdy `fLong` jest `TRUE`, Metoda ta może również udostępniać parametrów funkcji i inne istotne informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame, interfejs](../../winscript/reference/idebugstackframe-interface.md)