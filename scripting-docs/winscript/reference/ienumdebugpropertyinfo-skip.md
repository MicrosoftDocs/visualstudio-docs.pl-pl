---
title: IEnumDebugPropertyInfo::Skip | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7544b8ea54fabc53e6c8476648e339c53da94d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963393"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Pomija określoną liczbę `DebugPropertyInfo` struktur w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `DebugPropertyInfo` struktur w kolejności wyliczenie, aby pominąć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`. Zwraca `S_FALSE` i ustawia bieżący wskaźnik element na koniec wyliczenia, jeśli `celt` jest większa niż liczba elementów w lewo w moduł wyliczający.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugPropertyInfo Interface](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)