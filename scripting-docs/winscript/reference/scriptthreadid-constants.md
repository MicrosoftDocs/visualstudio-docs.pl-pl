---
title: Stałe SCRIPTTHREADID | Microsoft Docs
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
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575671"
---
# <a name="scriptthreadid-constants"></a>Stałe SCRIPTTHREADID
Służy do określania typu wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Aktualnie wykonywany wątek.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Wątek podstawowy; oznacza to, że wątek, w którym utworzono wystąpienie aparatu skryptów.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Wszystkie wątki.|  
  
## <a name="remarks"></a>Uwagi  
 Typ `SCRIPTTHREADID` jest używany przez `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` i `IActiveScript::InterruptScriptThread`, ale stałe mogą być używane tylko przez `IActiveScript::GetScriptThreadState` i `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)    
 [IActiveScript:: GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)    
 [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)    
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)