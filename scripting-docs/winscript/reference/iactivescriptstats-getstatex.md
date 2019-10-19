---
title: 'IActiveScriptStats:: GetStatEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576123"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Zwraca statystykę niestandardowego skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 podczas Określa, która Statystyka ma zostać zwrócona. Semantyka, której Statystyka odnosi się do określonego identyfikatora GUID, ma całkowicie zdefiniowany aparat.  
  
 `pluHi`  
 określoną Wysoka 32 bitów 64-bitowej liczby całkowitej bez znaku reprezentująca statystykę.  
  
 `pluLo`  
 określoną Niska 32 bitów z 64-bitową liczbą całkowitą bez znaku reprezentującą statystykę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia aparatowi skryptu niestandardowego zwracanie statystyk istotnych dla hosta niestandardowego.  
  
> [!NOTE]
> Ta metoda nie jest obecnie zaimplementowana.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptStats:: getstat](../../winscript/reference/iactivescriptstats-getstat.md)    
 [IActiveScriptStats, interfejs](../../winscript/reference/iactivescriptstats-interface.md)