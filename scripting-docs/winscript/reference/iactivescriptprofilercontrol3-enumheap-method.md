---
title: Metoda IActiveScriptProfilerControl3::EnumHeap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6120b8fdd913b4acee2e3ee6774d770aa75b1f5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992965"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>Metoda IActiveScriptProfilerControl3::EnumHeap
Zwraca interfejs ([interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) który może służyć do iteracji na obiektach sterty GC w kontekście aparatu obsługi skryptów skojarzonych.  
  
 Można wywołać tę metodę w każdym debugowaniu lub trybie wersji. Ta metoda powinna być wywoływana, gdy wątek interfejsu użytkownika jest bezczynny. Po wywołaniu metody żadne operacje nie powinny były wykonywane wbrew aparat skryptu, z wyjątkiem [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) aż [metoda IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)zwraca S_FALSE lub [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) zwolnieniu wskaźnika interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppEnum  
 [out] Zwraca [interfejs IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT.