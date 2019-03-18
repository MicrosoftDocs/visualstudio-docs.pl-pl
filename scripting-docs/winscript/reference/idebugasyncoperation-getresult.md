---
title: IDebugAsyncOperation::GetResult | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 49cf761c85fce3f8fc2f6705d114ab042e0c2ecd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58158003"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Zawiera wartości zwracanej i parametru zwracanego obiektu z operacji synchronicznych debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 [out] Jeśli operacja została zakończona, `phrResult` jest zwracana wartość `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Jeśli operacja została zakończona, `ppunkResult` parametr obiekt zwrócony przez operację.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Operacja nie zostanie ukończona.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli operacja zostanie ukończona, Metoda ta zwraca `HRESULT` obiekt parametr `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)