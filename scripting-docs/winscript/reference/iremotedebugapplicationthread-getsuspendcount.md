---
title: IRemoteDebugApplicationThread::GetSuspendCount | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetSuspendCount
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetSuspendCount
ms.assetid: 37f9936c-fd7c-412d-9a7f-628ca3a90438
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9df531e1abc5474bd21f58c29a3a2907086e20a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788107"
---
# <a name="iremotedebugapplicationthreadgetsuspendcount"></a>IRemoteDebugApplicationThread::GetSuspendCount
Zwraca wstrzymania liczenia dla wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetSuspendCount(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwCount`  
 [out] Wstrzymania liczenia wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wstrzymania liczenia dla wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplicationThread, interfejs](../../winscript/reference/iremotedebugapplicationthread-interface.md)