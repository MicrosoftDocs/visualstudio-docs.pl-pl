---
title: 'IActiveScriptProfilerCallback2:: OnFunctionEnterByName | Microsoft Docs'
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
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571636"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Powiadamia obiekt profilera, że aparat skryptów wykonuje wywołanie funkcji Document Object Model (DOM).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 podczas Nazwa funkcji, która ma zostać wykonana przez aparat wykonywania skryptów.  
  
 `scriptType`  
 podczas Typ funkcji. Aby uzyskać opisy prawidłowych wartości, zobacz [Wyliczenie PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość tej metody jest ignorowana przez aparat wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wywołań modelu DOM aparat skryptów wywołuje tę metodę zamiast wywoływania [IActiveScriptProfilerCallback:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Wynika to z dużej liczby unikatowych metod i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerCallback2:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)    
 [IActiveScriptProfilerCallback2, interfejs](../../winscript/reference/iactivescriptprofilercallback2-interface.md)