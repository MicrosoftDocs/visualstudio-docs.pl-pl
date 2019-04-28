---
title: IEnumDebugPropertyInfo::Next | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1568d2387422bebc86ce2b035ba997610833e85
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963419"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Pobiera określoną liczbę `DebugPropertyInfo` struktur w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `DebugPropertyInfo`struktur, które mają zostać pobrane.  
  
 `rgelt`  
 [out] Tablica `DebugPropertyInfo` struktury pobierane.  
  
 `pceltFetched`  
 [out] Zwraca liczbę `DebugPropertyInfo` struktury faktycznego pobrania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugPropertyInfo Interface](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo, struktura](../../winscript/reference/debugpropertyinfo-structure.md)