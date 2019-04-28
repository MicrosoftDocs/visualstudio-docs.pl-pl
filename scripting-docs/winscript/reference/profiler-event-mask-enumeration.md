---
title: Wyliczenie PROFILER_EVENT_MASK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7230e65e5559d53e56cf6424a34dd44aa4edda7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831645"
---
# <a name="profilereventmask-enumeration"></a>Wyliczenie PROFILER_EVENT_MASK
Określa typy zdarzeń, które powinny być profilowane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Funkcje profilów, które są zdefiniowane w skrypt napisany przez użytkownika i kod dynamicznych.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Profile natywne funkcje, które są definiowane przez silnik wykonywania skryptów.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Profiluje wszystkie funkcje aparatu skryptów i zdefiniowanych przez użytkownika, z wyłączeniem wywołania do modelu DOM (Document Object).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Funkcje profilów, które wywołują DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Profiluje wszystkie funkcje, w tym wywołaniami DOM.|  
  
## <a name="see-also"></a>Zobacz też  
 [Aktywnego skryptu Profiler stałe, wyliczenia i struktury](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)