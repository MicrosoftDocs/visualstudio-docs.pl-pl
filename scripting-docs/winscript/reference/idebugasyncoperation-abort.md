---
title: 'IDebugAsyncOperation:: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573299"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Anuluje operację.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|S_OK|Wykonanie metody powiodło się.|  
|E_NOTIMPL|Nie można anulować operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zwykle wywoływana z poziomu wątku debugera, aby anulować operację, która nie odpowiada. Ta metoda powoduje wywoływanie metody `InProgressAbort` w obiekcie `IDebugSyncOperation`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugAsyncOperation  interfejsu](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugAsyncOperation:: Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)