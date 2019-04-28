---
title: IDebugCodeContext::SetBreakPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7bbfe38c1db9f7c9afff34f5a92b8c43b0f4f9ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974530"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Ustawia lub czyści punkt przerwania w tym kontekście kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bps`  
 [in] Określa stan punktu przerwania dla tego kontekstu kodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustawia lub czyści punkt przerwania w tym kontekście kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT_STATE, wyliczenie](../../winscript/reference/breakpoint-state-enumeration.md)