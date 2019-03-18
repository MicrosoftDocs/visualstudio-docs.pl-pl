---
title: IRemoteDebugApplicationEvents::OnLeaveBreakPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnLeaveBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnLeaveBreakPoint
ms.assetid: 00449a23-1f67-4078-ad06-4c426abf7587
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f10ffdd19abd2aada2a98d6d0ae523686abb2e7e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159468"
---
# <a name="iremotedebugapplicationeventsonleavebreakpoint"></a>IRemoteDebugApplicationEvents::OnLeaveBreakPoint
Obsługuje zdarzenie opuszczania punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnLeaveBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prdat`  
 [in] Wątek aplikacji, która pozostanie punkt przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie opuszczania punktu przerwania.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplicationEvents, interfejs](../../winscript/reference/iremotedebugapplicationevents-interface.md)