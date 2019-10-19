---
title: 'IDebugExpression:: GetResultAsDebugProperty | Microsoft Docs'
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
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575929"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Zwraca wynik obliczania wyrażenia jako właściwość Debug i wartość zwracaną operacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 określoną Wartość zwracana przez operację.  
  
 `ppdp`  
 określoną Właściwość Debug dla wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Operacja jest nadal w stanie oczekiwania.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wynik oceny wyrażenia jako `IDebugProperty` i `HRESULT` operacji.  
  
 Ta metoda zwraca `S_OK` i `phrResult` zwraca `E_ABORT` Jeśli `Abort` przerywa operację.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugExpression   interfejsu](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)