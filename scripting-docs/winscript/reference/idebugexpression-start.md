---
title: 'IDebugExpression:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576430"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Rozpoczyna Obliczanie wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdecb`  
 podczas Wywołanie zwrotne wskazujące, kiedy szacowanie wyrażeń zostało zakończone. Jeśli ten parametr jest `NULL`, żadne zdarzenia nie są uruchamiane i klient musi sondować stan wyrażenia przy użyciu `QueryIsComplete`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda rozpoczyna Obliczanie wyrażenia.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugExpression:: Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression, interfejs](../../winscript/reference/idebugexpression-interface.md)