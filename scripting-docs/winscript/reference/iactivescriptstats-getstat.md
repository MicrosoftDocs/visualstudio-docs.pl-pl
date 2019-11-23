---
title: 'IActiveScriptStats:: getstat | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574339"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Zwraca jedną z statystyk standardowego skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stid`  
 podczas Określa, która Statystyka ma zostać zwrócona. Musi być wartością:  
  
|Stała|Value|Opis|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Zwróć liczbę instrukcji wykonanych od momentu uruchomienia skryptu lub wartości statystycznych, które zostały zresetowane.|  
  
 `pluHi`  
 określoną Wysoka 32 bitów 64-bitowej liczby całkowitej bez znaku reprezentująca statystykę.  
  
 `pluLo`  
 określoną Niska 32 bitów z 64-bitową liczbą całkowitą bez znaku reprezentującą statystykę.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Możliwe wartości obejmują, ale nie są ograniczone do wartości w poniższej tabeli.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca jedną z statystyk standardowego skryptu.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats, interfejs](../../winscript/reference/iactivescriptstats-interface.md)