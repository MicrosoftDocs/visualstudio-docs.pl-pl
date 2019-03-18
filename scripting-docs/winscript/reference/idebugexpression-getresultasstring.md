---
title: IDebugExpression::GetResultAsString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84255e364630245564a0cbab5d38c6dff38df0a8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146594"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Zwraca wynik obliczania wyrażenia jako ciąg i wartości zwracanej wykonać operację.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 [out] Wartość zwracana wykonać operację.  
  
 `pbstrResult`  
 [out] Wynik obliczania wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Ta operacja jest nadal oczekujące.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wynik obliczania wyrażenia jako ciąg i wykonać operację `HRESULT`.  
  
 Ta metoda zwraca `S_OK` i `phrResult` zwraca `E_ABORT` Jeśli `Abort` przerywa operację.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpression, interfejs](../../winscript/reference/idebugexpression-interface.md)