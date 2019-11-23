---
title: 'IDebugApplication:: SynchronousCallInDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574587"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Zapewnia mechanizm wywołujący, aby uruchomić kod w wątku debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pptc`  
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
 Aparaty i hosty języka zwykle używają tej metody do implementowania obiektów wolnych wątków na podstawie ich wielowątkowych implementacji.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication  interfejsu](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugThreadCall, interfejs](../../winscript/reference/idebugthreadcall-interface.md)