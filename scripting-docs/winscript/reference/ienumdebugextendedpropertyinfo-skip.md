---
title: 'IEnumDebugExtendedPropertyInfo:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e5c187f3484154a2758b67300c98d4cb9fc9023
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574242"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
Pomija określoną liczbę struktur `ExtendedDebugPropertyInfo` w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba struktur `ExtendedDebugPropertyInfo` w sekwencji wyliczenia do pominięcia.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`. Zwraca `S_FALSE` i ustawia bieżący wskaźnik elementu na koniec wyliczenia, jeśli `celt` jest większa niż liczba elementów pozostawionych w module wyliczającym.  
  
## <a name="see-also"></a>Zobacz także  
 [IEnumDebugExtendedPropertyInfo  interfejsu](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)  
 [ExtendedDebugPropertyInfo, struktura](../../winscript/reference/extendeddebugpropertyinfo-structure.md)