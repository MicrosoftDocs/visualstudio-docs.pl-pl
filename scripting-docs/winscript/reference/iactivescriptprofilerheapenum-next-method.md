---
title: Metoda IActiveScriptProfilerHeapEnum::Next | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4bad607db168d5f3e3533087c94c6c0970f5eb24
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992819"
---
# <a name="iactivescriptprofilerheapenumnext-method"></a>Metoda IActiveScriptProfilerHeapEnum::Next
Pobiera następny obiekt lub obiekty w zestawie obiektów sterty z [metoda IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Next (    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,     [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 Liczba obiektów, które mają zostać zwrócone.  
  
 `heapObjects`  
 [out] Następne [PROFILER_HEAP_OBJECT, struktura](../../winscript/reference/profiler-heap-object-structure.md) struktury.  
  
 `pceltFetched`  
 [out] Liczba obiektów zwróconych,  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT.