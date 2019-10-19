---
title: 'IEnumDebugApplicationNodes:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4ad47c0119eb46c05368fa40ba3a5965fecce0b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573050"
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
Pobiera określoną liczbę segmentów w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba segmentów do pobrania.  
  
 `pprddp`  
 określoną Zwraca tablicę `IDebugApplicationNode` interfejsów, które reprezentują segmenty, które są pobierane.  
  
 `pceltFetched`  
 określoną Rzeczywista liczba segmentów pobranych przez moduł wyliczający.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera określoną liczbę segmentów w sekwencji wyliczenia.  
  
## <a name="see-also"></a>Zobacz także  
 [IEnumDebugApplicationNodes, interfejs](../../winscript/reference/ienumdebugapplicationnodes-interface.md)