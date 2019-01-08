---
title: IDebugApplicationThread::SynchronousCallIntoThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e5e25f42b2bce66cf3bb7ab3e69d3711e2526ae1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097061"
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