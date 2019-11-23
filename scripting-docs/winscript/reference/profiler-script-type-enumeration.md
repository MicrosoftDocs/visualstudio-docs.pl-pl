---
title: Wyliczenie PROFILER_SCRIPT_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574568"
---
# <a name="profiler_script_type-enumeration"></a>Wyliczenie PROFILER_SCRIPT_TYPE Enumeration
Określa typ skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Określa kod skryptu zarejestrowanego przez użytkownika.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Określa kod skryptu, który jest generowany dynamicznie podczas wykonywania.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Określa typ skryptu dla natywnych funkcji i obiektów, które są zdefiniowane przez aparat obsługi skryptów.|  
|PROFILER_SCRIPT_TYPE_DOM|Określa wywołanie do Document Object Model (DOM) programu Internet Explorer, na przykład wywołanie metody `document.getElementById`.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)