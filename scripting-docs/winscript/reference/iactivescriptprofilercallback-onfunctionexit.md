---
title: 'IActiveScriptProfilerCallback:: OnFunctionExit | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571671"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Powiadamia obiekt profilera, że aparat skryptów zakończył wywołanie funkcji, która nie jest wywołaniem do Document Object Model (DOM).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 podczas Unikatowy identyfikator skryptu, do którego należy ta funkcja. Ten identyfikator jest przypisywany przez aparat obsługi skryptów.  
  
 `functionId`  
 podczas Unikatowy identyfikator funkcji. Ten identyfikator jest przypisywany przez aparat obsługi skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość tej metody jest ignorowana przez aparat wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wywołań modelu DOM aparat skryptów wywołuje [IActiveScriptProfilerCallback2:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) , a nie `IActiveScriptProfilerCallback::OnFunctionExit`. Wynika to z dużej liczby unikatowych metod i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerCallback:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)