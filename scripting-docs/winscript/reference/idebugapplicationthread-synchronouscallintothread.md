---
title: 'IDebugApplicationThread:: SynchronousCallIntoThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574501"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Zapewnia mechanizm wywołujący do uruchamiania kodu w wątku aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstcb`  
 podczas Obiekt, który ma zostać wywołany.  
  
 `dwParam1`  
 podczas Pierwszy parametr do przekazania do metody `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 podczas Drugi parametr, który zostanie przekazany do metody `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 podczas Trzeci parametr do przekazania do metody `IDebugThreadCall::ThreadCallHandler`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia mechanizm wywołujący do uruchamiania kodu w wątku debugera. Aparaty i hosty języka zwykle używają tej metody do implementowania obiektów wolnych wątków na podstawie ich wielowątkowych implementacji.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationThread  interfejsu](../../winscript/reference/idebugapplicationthread-interface.md)  
 [IDebugThreadCall, interfejs](../../winscript/reference/idebugthreadcall-interface.md)