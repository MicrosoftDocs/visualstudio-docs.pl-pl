---
title: Stałe SCRIPTTHREADID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfbb39d10d552141a68d40a7be3f1715a80f8f57
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58158055"
---
# <a name="scriptthreadid-constants"></a>Stałe SCRIPTTHREADID
Umożliwia określenie typu wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Aktualnie wykonywany wątek.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Podstawowy wątek; oznacza to wątek, w którym skryptów aparatu została utworzona.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Wszystkie wątki.|  
  
## <a name="remarks"></a>Uwagi  
 `SCRIPTTHREADID` Typ jest używany przez `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, i `IActiveScript::InterruptScriptThread`, ale stałe mogą być używane tylko przez `IActiveScript::GetScriptThreadState` i `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)