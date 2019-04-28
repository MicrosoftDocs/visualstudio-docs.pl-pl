---
title: IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnBreakFlagChange
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb19b6cfc423a1305276441305ef854c70f2d896
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943787"
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Obsługuje zdarzenie po zmianie flag podziału.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `abf`  
 [in] Bieżące flagi przerwania dla aplikacji.  
  
 `prdatSteppingThread`  
 [in] Aktualnie uruchomionemu wątkowi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie, gdy zmienią się Flaga podziału.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplicationEvents Interface](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [APPBREAKFLAGS, wyliczenie](../../winscript/reference/appbreakflags-enumeration.md)