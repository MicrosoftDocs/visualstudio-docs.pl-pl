---
title: IDebugApplication::SynchronousCallInDebuggerThread | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d5460efaa3448c7812707e0baa7b2f5afe1d27a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990554"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Udostępnia mechanizm do obiektu wywołującego uruchomić kod w wątku debugera.  
  
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
 Aparaty języka i hosty zazwyczaj ta metoda umożliwia Implementowanie bezwątkowy obiektów na podstawie ich pojedynczej implementacji wątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall, interfejs](../../winscript/reference/idebugthreadcall-interface.md)