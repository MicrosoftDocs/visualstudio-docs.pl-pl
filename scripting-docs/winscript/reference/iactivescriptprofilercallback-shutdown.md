---
title: 'IActiveScriptProfilerCallback:: Shutdown | Microsoft Docs'
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
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571648"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Wywołuje się, by poinformować obiekt profilera za każdym razem, gdy profilowanie zostanie zatrzymane w aparacie skryptów. W ten sposób obiekt profilera może wywoływać procedury czyszczenia, jeśli jest to wymagane. Ta metoda jest również wywoływana przez aparat skryptów podczas zamykania aparatu skryptów lub gdy wywołanie [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) kończy się niepowodzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hrReason`  
 podczas Przyczyna zamknięcia. Jeśli aparat skryptów jest zamykany, `S_OK` jest przenoszona. Jeśli wywołanie [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) zwraca błąd HRESULT, zostanie przeniesiona wartość HRESULT. W przeciwnym razie ta wartość jest pobierana z [IActiveScriptProfilerControl:: StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość tej metody jest ignorowana przez aparat wykonywania skryptów.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)