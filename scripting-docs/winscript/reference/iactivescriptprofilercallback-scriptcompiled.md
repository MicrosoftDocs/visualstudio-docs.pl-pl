---
title: IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs
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
ms.openlocfilehash: a198667e7dc30969c32b556620b139d52f833543
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993238"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Powiadamia program profilujący, że obiekt, który aparat skryptów skompilowany skrypt. Ta metoda jest wywoływana dla każdego skryptu, który jest kompilowany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 [in] Unikatowy identyfikator skryptu, który został skompilowany. Ten identyfikator jest przypisywany przez silnik wykonywania skryptów.  
  
 `type`  
 [in] Typ skryptu, który został skompilowany. Wartości są zdefiniowane w [wyliczenie profiler_script_type Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Jeśli to możliwe, wskaźnik do `IUnknown` interfejs, który program profilujący musi szukać [interfejs IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) wskaźnika. W przeciwnym razie będzie pusta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana przez tę metodę jest ignorowana przez silnik wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów może zapewnić kontekstu dokumentu, tylko wtedy, gdy jest to obsługiwane przez hosta.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)