---
title: Wyliczenie profiler_script_type Enumeration | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ac387af4601ff822982c10e61f9813b2db7e8047
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086913"
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