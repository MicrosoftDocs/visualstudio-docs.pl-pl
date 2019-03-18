---
title: IDebugApplicationThread::SynchronousCallIntoThread | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f0c9b89332b55a180220820e8ffe1e030d37a848
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146711"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Udostępnia mechanizm do obiektu wywołującego uruchomić kod w wątku aplikacji.  
  
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
 [in] Obiekt do wywołania.  
  
 `dwParam1`  
 [in] Pierwszy parametr do przekazania do `IDebugThreadCall::ThreadCallHandler` metody.  
  
 `dwParam2`  
 [in] Drugi parametr do przekazania do `IDebugThreadCall::ThreadCallHandler` metody.  
  
 `dwParam3`  
 [in] Trzeci parametr do przekazania do `IDebugThreadCall::ThreadCallHandler` metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia mechanizm do obiektu wywołującego uruchomić kod w wątku debugera. Aparaty języka i hosty zazwyczaj ta metoda umożliwia Implementowanie bezwątkowy obiektów na podstawie ich pojedynczej implementacji wątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall, interfejs](../../winscript/reference/idebugthreadcall-interface.md)