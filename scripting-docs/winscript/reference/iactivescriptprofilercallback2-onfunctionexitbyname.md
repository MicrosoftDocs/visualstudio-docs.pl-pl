---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87f0b7e7a3cea4e3e59fb43ef9ddc2d4934552e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993348"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Powiadamia program profilujący, że obiekt, który aparat skryptów Zakończono wywołanie funkcji Document Object Model (DOM).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 [in] Nazwa funkcji, że aparat skryptów zakończeniu pracy.  
  
 `scriptType`  
 [in] Typ funkcji. Opisy prawidłowych wartości można znaleźć [wyliczenie profiler_script_type Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana przez tę metodę jest ignorowana przez silnik wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Dla połączeń modelu DOM, aparat skryptów wywołuje tę metodę, zamiast wywoływać metodę [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Jest to spowodowane dużą liczbą unikatowy metod i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2, interfejs](../../winscript/reference/iactivescriptprofilercallback2-interface.md)