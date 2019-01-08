---
title: IActiveScriptProfilerCallback::FunctionCompiled | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4bd032914605c61b13a0a56a42e510c2af252f7e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091406"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Powiadamia program profilujący, że obiekt, który aparat skryptów napotkał funkcję, podczas kompilacji skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Unikatowy identyfikator funkcji. Ten identyfikator jest przypisywany przez silnik wykonywania skryptów.  
  
 `scriptId`  
 [in] Unikatowy identyfikator skryptu, który jest ona częścią.  
  
 `pwszFunctionName`  
 [in] Nazwa funkcji, lub wartość null dla funkcja anonimowa.  
  
 `pwszFunctionNameHint`  
 [in] Wywnioskowanej nazwy funkcji lub wartość null, jeśli silnik wykonywania skryptów nie są rozpoznawane przez dowolną nazwę.  
  
 `pIDebugDocumentContext`  
 [in] Jeśli to możliwe, wskaźnik do `IUnknown` interfejs, który program profilujący musi szukać [interfejs IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) wskaźnika. W przeciwnym razie wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana przez tę metodę jest ignorowana przez silnik wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów może zapewnić kontekstu dokumentu, tylko wtedy, gdy jest to obsługiwane przez hosta.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)