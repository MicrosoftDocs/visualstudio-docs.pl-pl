---
title: IActiveScriptStats::GetStat | Microsoft Docs
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
ms.openlocfilehash: 8befb3da4e4b6f060a5f58aedec3604afe70aefb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159052"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Zwraca jedną z statystyki skrypt standardowy.  
  
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
 [in] Określa statystykę do zwrócenia. Musi mieć wartość:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Zwróć liczbę instrukcje wykonywane od chwili uruchomienia skryptu lub statystyki zostały zresetowane.|  
  
 `pluHi`  
 [out] Wysoka 32 bity 64-bitowa liczba całkowita bez znaku reprezentujący dane statystyczne.  
  
 `pluLo`  
 [out] Niski 32 bity 64-bitowa liczba całkowita bez znaku reprezentujący dane statystyczne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Możliwe wartości obejmują, ale nie są ograniczone do wartości w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca jeden z statystyki skrypt standardowy.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats, interfejs](../../winscript/reference/iactivescriptstats-interface.md)