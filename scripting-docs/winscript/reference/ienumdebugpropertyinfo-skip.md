---
title: 'IEnumDebugPropertyInfo:: Skip | Microsoft Docs'
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
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574157"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Pomija określoną liczbę struktur `DebugPropertyInfo` w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba struktur `DebugPropertyInfo` w sekwencji wyliczenia do pominięcia.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`. Zwraca `S_FALSE` i ustawia bieżący wskaźnik elementu na koniec wyliczenia, jeśli `celt` jest większa niż liczba elementów pozostawionych w module wyliczającym.  
  
## <a name="see-also"></a>Zobacz także  
 [IEnumDebugPropertyInfo  interfejsu](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)