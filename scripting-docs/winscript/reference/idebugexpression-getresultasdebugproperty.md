---
title: IDebugExpression::GetResultAsDebugProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06d9b513d40450e20bb87f07c460bef7ce2678c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978500"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Zwraca wynik obliczania wyrażenia jako właściwość debugowania i wartość zwracana wykonać operację.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 [out] Wartość zwracana wykonać operację.  
  
 `ppdp`  
 [out] Właściwości debugowania dla wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Ta operacja jest nadal oczekujące.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wynik obliczania wyrażenia jako `IDebugProperty` i wykonać operację `HRESULT`.  
  
 Ta metoda zwraca `S_OK` i `phrResult` zwraca `E_ABORT` Jeśli `Abort` przerywa operację.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugExpression](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)