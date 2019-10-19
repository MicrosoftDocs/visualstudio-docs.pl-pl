---
title: 'IActiveScriptProfilerCallback:: ScriptCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571662"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Powiadamia obiekt profilera, że aparat skryptów skompilowan skrypt. Ta metoda jest wywoływana dla każdego skompilowanego skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 podczas Unikatowy identyfikator skompilowanego skryptu. Ten identyfikator jest przypisywany przez aparat obsługi skryptów.  
  
 `type`  
 podczas Typ skryptu, który został skompilowany. Wartości są zdefiniowane w [wyliczeniu PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 podczas Jeśli jest dostępny, wskaźnik do interfejsu `IUnknown`, który profiler musi wykonać zapytanie o wskaźnik [interfejsu IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) . W przeciwnym razie będzie to miało wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość tej metody jest ignorowana przez aparat wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Aparat obsługi skryptów może udostępnić kontekst dokumentu tylko wtedy, gdy jest obsługiwany przez hosta.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)