---
title: IActiveScriptProfilerControl5::EnumHeap2, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c90c536dee76d67fdb93dd205e8f6eedff6dcc7
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58150806"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 — Metoda
Zwraca interfejs ([interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) który może służyć do iteracji na obiektach sterty GC w kontekście aparatu obsługi skryptów skojarzonych.  
  
 Można wywołać tę metodę w każdym debugowaniu lub trybie wersji. Ta metoda powinna być wywoływana, gdy wątek interfejsu użytkownika jest bezczynny. Po wywołaniu metody żadne operacje nie powinny były wykonywane wbrew aparat skryptu, z wyjątkiem [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) aż [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)zwraca S_FALSE lub [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) zwolnieniu wskaźnika interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 enumFlags  
 Wartość określająca, czy dodatkowe informacje o obiekcie wskazanym w relacji obiektu jest widoczna. Dodatkowe informacje może wskazywać, czy obiekt wskazany jest metodą pobierającą czy ustawiającą. Aby uzyskać więcej informacji, zobacz [PROFILER_HEAP_ENUM_FLAGS, wyliczenie](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Zwraca [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wyliczenie sterty, zostało ukończone pomyślnie.|  
|`E_OUTOFMEMORY`|Nie był wystarczająco dużo dostępnej pamięci do przeprowadzenia wyliczenie sterty.|  
|`E_FAIL`|Wystąpił błąd wewnętrzny.|