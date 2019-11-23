---
title: 'IDebugCodeContext:: setpunkt przerwania | Microsoft Docs'
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
ms.openlocfilehash: df2bb0395cc1aeaceda3763b2c4016bbd9ba7e1f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573208"
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
 podczas Określa stan punktu przerwania dla tego kontekstu kodu.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustawia lub czyści punkt przerwania w tym kontekście kodu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugCodeContext  interfejsu](../../winscript/reference/idebugcodecontext-interface.md)  
 [BREAKPOINT_STATE, wyliczenie](../../winscript/reference/breakpoint-state-enumeration.md)