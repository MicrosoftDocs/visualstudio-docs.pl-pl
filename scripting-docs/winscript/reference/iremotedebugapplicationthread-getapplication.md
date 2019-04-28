---
title: IRemoteDebugApplicationThread::GetApplication | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetApplication
ms.assetid: 9446c7f9-cfa2-408f-98c5-64f549783de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abe33d75f7e03944eb0a6f533f2955871ddee342
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788235"
---
# <a name="iremotedebugapplicationthreadgetapplication"></a>IRemoteDebugApplicationThread::GetApplication
Zwraca obiekt aplikacji skojarzonych z tym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetApplication(  
   IRemoteDebugApplication**  pprda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pprda`  
 [out] Obiekt aplikacji skojarzonych z tym wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca obiekt aplikacji skojarzonych z tym wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplicationThread, interfejs](../../winscript/reference/iremotedebugapplicationthread-interface.md)