---
title: 'IActiveScriptProfilerCallback:: FunctionCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576475"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Powiadamia obiekt profilera, że aparat skryptów napotkał funkcję podczas kompilowania skryptu.  
  
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
 podczas Unikatowy identyfikator funkcji. Ten identyfikator jest przypisywany przez aparat obsługi skryptów.  
  
 `scriptId`  
 podczas Unikatowy identyfikator skryptu, do którego należy ta funkcja.  
  
 `pwszFunctionName`  
 podczas Nazwa funkcji lub wartość null dla funkcji anonimowej.  
  
 `pwszFunctionNameHint`  
 podczas Wywnioskowana nazwa funkcji lub wartość null, jeśli aparat skryptów nie wywnioskuje żadnej nazwy.  
  
 `pIDebugDocumentContext`  
 podczas Jeśli jest dostępny, wskaźnik do interfejsu `IUnknown`, który profiler musi wykonać zapytanie o wskaźnik [interfejsu IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) . W przeciwnym razie wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość tej metody jest ignorowana przez aparat wykonywania skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Aparat obsługi skryptów może udostępnić kontekst dokumentu tylko wtedy, gdy jest obsługiwany przez hosta.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerCallback, interfejs](../../winscript/reference/iactivescriptprofilercallback-interface.md)