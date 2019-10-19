---
title: 'IEnumDebugStackFrames:: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Clone
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f812176406b234160883956c3311d8c05a75b743
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570882"
---
# <a name="ienumdebugstackframesclone"></a>IEnumDebugStackFrames::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan co bieżący moduł wyliczający.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppedsf`  
 określoną Zwraca interfejs `IEnumDebugStackFrames` klonowania modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy moduł wyliczający, który zawiera ten sam stan co bieżący moduł wyliczający.  
  
## <a name="see-also"></a>Zobacz także  
 [IEnumDebugStackFrames, interfejs](../../winscript/reference/ienumdebugstackframes-interface.md)