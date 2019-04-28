---
title: Wyliczenie profiler_script_type Enumeration | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ca90a566db422d75fefc44267ffe10504bb872ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816788"
---
# <a name="profilerscripttype-enumeration"></a>Wyliczenie PROFILER_SCRIPT_TYPE Enumeration
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Określa kod, skrypt napisany przez użytkownika.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Określa kod skryptu, który jest generowany dynamicznie podczas wykonywania.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Określa typ skryptu dla natywnej funkcji i obiektów, które są definiowane przez silnik wykonywania skryptów.|  
|PROFILER_SCRIPT_TYPE_DOM|Określa wywołanie do modelu DOM (Document Object) programu Internet Explorer, na przykład, wywołanie `document.getElementById` metody.|  
  
## <a name="see-also"></a>Zobacz też  
 [Aktywnego skryptu Profiler stałe, wyliczenia i struktury](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)