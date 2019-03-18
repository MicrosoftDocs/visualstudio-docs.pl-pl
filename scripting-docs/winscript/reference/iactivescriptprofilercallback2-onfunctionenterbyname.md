---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6fdb4addace1b0bbabdd4303c3943b976763514
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146100"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Powiadamia obiekt profiler, który silnik wykonywania skryptów przechodzi do wykonania wywołania funkcji z modelu DOM (Document Object).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 [in] Nazwa funkcji, która silnik wykonywania skryptów przechodzi do wykonania.  
  
 `scriptType`  
 [in] Typ funkcji. Opisy prawidłowych wartości można znaleźć [wyliczenie profiler_script_type Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana przez tę metodę jest ignorowana przez silnik wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Dla połączeń modelu DOM, aparat skryptów wywołuje tę metodę, zamiast wywoływać metodę [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Jest to spowodowane dużą liczbą unikatowy metod i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2, interfejs](../../winscript/reference/iactivescriptprofilercallback2-interface.md)