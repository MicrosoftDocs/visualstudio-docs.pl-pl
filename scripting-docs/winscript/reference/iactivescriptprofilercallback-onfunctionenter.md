---
title: 'IActiveScriptProfilerCallback:: OnFunctionEnter | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571686"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Powiadamia obiekt profilera, że aparat skryptów ma wykonać wywołanie funkcji, które nie jest wywołaniem do Document Object Model (DOM).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnFunctionEnter(  
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
 W przypadku wywołań modelu DOM aparat skryptów wywołuje [IActiveScriptProfilerCallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) , a nie `IActiveScriptProfilerCallback::OnFunctionEnter`. Wynika to z dużej liczby unikatowych metod i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerCallback:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)    
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)