---
title: IRemoteDebugApplicationThread::GetDescription | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetDescription
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetDescription
ms.assetid: 69842e9e-7c1c-4841-a6b2-31505fe85738
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c60e12eef269da46aea317611cb06223d0811ddc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788199"
---
# <a name="iremotedebugapplicationthreadgetdescription"></a>IRemoteDebugApplicationThread::GetDescription
Pobiera opis i stan tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription,  
   BSTR*  pbstrState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrDescription`  
 [out] Opis tego wątku.  
  
 `pbstrState`  
 [out] Opis stan wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera opis i stan tego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplicationThread, interfejs](../../winscript/reference/iremotedebugapplicationthread-interface.md)