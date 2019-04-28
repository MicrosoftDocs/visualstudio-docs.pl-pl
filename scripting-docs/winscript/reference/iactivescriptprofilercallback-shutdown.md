---
title: IActiveScriptProfilerCallback::Shutdown | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091ccc30f16081fdca8f10778efec208ef5ccb16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993426"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Wywoływana, aby poinformować obiekt profiler po każdym zatrzymaniu profilowania na silnik wykonywania skryptów. W ten sposób obiekt profiler może wywołać jej procedury oczyszczania, jeśli jest to wymagane. Ta metoda jest również wywoływany przez silnik wykonywania skryptów, gdy silnik wykonywania skryptów jest zamykany lub wywołanie [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) zakończy się niepowodzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hrReason`  
 [in] Przyczyna zamykanie. Jeśli silnik wykonywania skryptów jest zamykana, `S_OK` jest przekazywany. Jeśli wywołanie [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) zwraca błąd HRESULT, jest przekazywany HRESULT. W przeciwnym razie ta wartość jest pobierana z [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana przez tę metodę jest ignorowana przez silnik wykonywania skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)