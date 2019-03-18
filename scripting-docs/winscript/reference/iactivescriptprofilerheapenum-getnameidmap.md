---
title: IActiveScriptProfilerHeapEnum::GetNameIdMap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3284557bf71a038d884c1f8786755b7761770e21
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157389"
---
# <a name="iactivescriptprofilerheapenumgetnameidmap"></a>IActiveScriptProfilerHeapEnum::GetNameIdMap
Zwraca nazwy ciąg odpowiadający [PROFILER_HEAP_OBJECT_NAME_ID, typ](../../winscript/reference/profiler-heap-object-name-id-type.md) wartości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetNameIdMap (    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],     [out] UINT *pcelt);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pNameList`  
 [out] Tablica nazw skojarzonych z [PROFILER_HEAP_OBJECT_NAME_ID, typ](../../winscript/reference/profiler-heap-object-name-id-type.md) wartości.  
  
 `pcelt`  
 [out] Liczba nazw w tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość HRESULT.