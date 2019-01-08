---
title: IActiveScriptProfilerCallback::ScriptCompiled | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bf653e5623506a68e6353e3d9f97077592e87941
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091510"
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