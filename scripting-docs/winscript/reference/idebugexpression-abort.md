---
title: 'IDebugExpression:: Abort | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Abort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Abort
ms.assetid: dbdb63c1-6c4a-4cef-bb40-1843495ae167
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 508939b23be53acbff269744ae4035853f977ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575934"
---
# <a name="idebugexpressionabort"></a>IDebugExpression::Abort
Kończy wyrażenie.  
  
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
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda przerywa Obliczanie wyrażenia w najkrótszej okazji.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugExpression  interfejsu](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)