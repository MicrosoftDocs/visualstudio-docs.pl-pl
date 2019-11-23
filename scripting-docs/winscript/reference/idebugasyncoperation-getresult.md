---
title: 'IDebugAsyncOperation:: GetResult | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573286"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Dostarcza wartość zwracaną i parametr obiektu zwrotnego z synchronicznej operacji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 określoną Jeśli operacja zostanie zakończona, `phrResult` jest wartością zwracaną `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 określoną Jeśli operacja zostanie zakończona, `ppunkResult` jest parametrem obiektu zwróconym przez operację.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Operacja nie została ukończona.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli operacja została ukończona, metoda zwraca `HRESULT` i parametr obiektu z `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugAsyncOperation  interfejsu](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)