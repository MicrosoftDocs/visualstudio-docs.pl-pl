---
title: IDebugApplicationThread::QueryIsDebuggerThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsDebuggerThread
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5594973f64446c0c6818522ad2ce2b174ab02610
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822166"
---
# <a name="idebugapplicationthreadqueryisdebuggerthread"></a>IDebugApplicationThread::QueryIsDebuggerThread
Określa, czy ten wątek jest debugera wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT QueryIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się i jest to wątek debugera.|  
|`S_FALSE`|Nie jest debugera wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy ten wątek wątek debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationThread, interfejs](../../winscript/reference/idebugapplicationthread-interface.md)