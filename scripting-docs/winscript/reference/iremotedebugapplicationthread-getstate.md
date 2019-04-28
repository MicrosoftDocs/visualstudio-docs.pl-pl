---
title: IRemoteDebugApplicationThread::GetState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6534f57c92776dcd3cde9083335becbd66002a32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788120"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Pobiera stan tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pState`  
 [out] Kombinacja następujących flag stan wątku:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Wątek jest uruchomiony.|  
|THREAD_STATE_SUSPENDED|0x00000002|Wątek jest zawieszony.|  
|THREAD_BLOCKED|0x00000004|Wątek jest zablokowany.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Ten wątek jest zawartość.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera stan tego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplicationThread, interfejs](../../winscript/reference/iremotedebugapplicationthread-interface.md)