---
title: Metoda IActiveScriptProfilerHeapEnum::GetOptionalInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab8096b79cfbb91e4b65256c84ab1ba01207d9ed
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146997"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>Metoda IActiveScriptProfilerHeapEnum::GetOptionalInfo
Pobiera informacje opcjonalne określonego obiektu (z zestawu sterty obiektów zwracanych z [metoda IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Nie powinna zwolnić zwrócone pamięć przypisana do zwracanych obiektów. Zamiast tego należy wywołać [metoda IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `heapObject`  
 [PROFILER_HEAP_OBJECT, struktura](../../winscript/reference/profiler-heap-object-structure.md) dla której ma zostać zwrócone informacje.  
  
 `celt`  
 Liczba [PROFILER_HEAP_OBJECT_OPTIONAL_INFO, struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md) struktury do zwrócenia.  
  
 `optionalInfo`  
 [out] Tablica [PROFILER_HEAP_OBJECT_OPTIONAL_INFO, struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md) struktury dla określonego obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT.