---
title: 'IRemoteDebugApplicationEvents:: OnBreakFlagChange | Microsoft Docs'
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
ms.openlocfilehash: 71e9a29b6dcc5cd6864ce4edffe9e5f96b64ba9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561706"
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Obsługuje zdarzenie po zmianie flag przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `abf`  
 podczas Bieżące flagi przerwania dla aplikacji.  
  
 `prdatSteppingThread`  
 podczas Aktualnie uruchomiony wątek.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie po zmianie flagi Break.  
  
## <a name="see-also"></a>Zobacz także  
 [IRemoteDebugApplicationEvents   interfejsu](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
 [APPBREAKFLAGS, wyliczenie](../../winscript/reference/appbreakflags-enumeration.md)