---
title: Aktywnego skryptu Profiler stałe, wyliczenia i struktury | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d39e6feb2cddd0c573368db9bf50b1e77f2e48d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58154728"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury profilera aktywnego skryptu
Następujące wyliczenia są używane przez aktywne interfejsy Profiler skryptu.  
  
## <a name="constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury  
  
|Stałe|Opis|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS, typ](../../winscript/reference/profiler-external-object-address-type.md)|Adres obiektu zewnętrznego programu profilującego. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) i [struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_ID, typ](../../winscript/reference/profiler-heap-object-id-type.md)|Identyfikator obiektu sterty. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[struktura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)i [Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_NAME_ID, typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identyfikator nazwy obiektu sterty. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Wyliczenia|Opis|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK, wyliczenie](../../winscript/reference/profiler-event-mask-enumeration.md)|Określa typy zdarzeń, które powinny być profilowane.|  
|[PROFILER_HEAP_ENUM_FLAGS, wyliczenie](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Flagi pokazujące, czy dodatkowe informacje o obiekcie sterty wskazanym w relacji obiektu jest widoczna. Używane w [IActiveScriptProfilerControl5::EnumHeap2, Metoda](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[PROFILER_HEAP_OBJECT_FLAGS, wyliczenie](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flagi, które reprezentują podstawowe informacje o obiekcie sterty. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE, wyliczenie](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Reprezentuje różne rodzaje informacji opcjonalnych. Używane w [struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[PROFILER_RELATIONSHIP_INFO, wyliczenie](../../winscript/reference/profiler-relationship-info-enumeration.md)|Reprezentuje informacje dotyczące obiektu w relacji. Używane w [struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_SCRIPT_TYPE, wyliczenie](../../winscript/reference/profiler-script-type-enumeration.md)|Określa typ skryptu.|  
  
|Struktury|Opis|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT, struktura](../../winscript/reference/profiler-heap-object-structure.md)|Przedstawia obiekty sterty są zbierane przez [metoda IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO, struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Reprezentuje opcjonalne informacje o obiektach sterty.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP, struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Reprezentuje relację obiekt sterty.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST, struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Reprezentuje listę relacje, które należą do obiekt sterty.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST, struktura](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Ta struktura jest skojarzony z tylko obiekty funkcyjne. Lista zakresów reprezentuje zamknięcia dla funkcji jako listę zakresów, gdzie każdy zakres jest obiekt sterty przy użyciu listy skojarzonej właściwości reprezentujący zmienne w każdej z danego zakresu. W niektórych przypadkach nazwy obiektów, w tym zakresie może nie być dostępna, tylko ich identyfikatorów.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO, struktura](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Przedstawia informacje o typie podciąg.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)