---
title: Stałe, wyliczenia i struktury profilera aktywnego skryptu | Microsoft Docs
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
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572695"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury profilera aktywnego skryptu
Następujące wyliczenia są używane przez interfejsy profilera aktywnego skryptu.  
  
## <a name="constants-enumerations-and-structures"></a>Stałe, wyliczenia i struktury  
  
|Stałe|Opis|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS, typ](../../winscript/reference/profiler-external-object-address-type.md)|Adres obiektu zewnętrznego profilera. Używany w [strukturze PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) i [strukturze PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_ID, typ](../../winscript/reference/profiler-heap-object-id-type.md)|Identyfikator obiektu sterty. Używany w strukturze [PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)struktura[PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), struktura [PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)i [Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_NAME_ID, typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identyfikator nazwy obiektu sterty. Używany w [strukturze PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Wyliczenia|Opis|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK, wyliczenie](../../winscript/reference/profiler-event-mask-enumeration.md)|Wskazuje typy zdarzeń, które powinny być profilowane.|  
|[PROFILER_HEAP_ENUM_FLAGS, wyliczenie](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Flagi, które reprezentują, czy dodatkowe informacje o obiekcie sterty wskazywanym w relacji obiektu są ujawniane. Używany w [metodzie IActiveScriptProfilerControl5:: EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[PROFILER_HEAP_OBJECT_FLAGS, wyliczenie](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flagi, które reprezentują podstawowe informacje o obiekcie sterty. Używany w [strukturze PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE, wyliczenie](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Reprezentuje różne typy dodatkowych informacji. Używany w [strukturze PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[PROFILER_RELATIONSHIP_INFO, wyliczenie](../../winscript/reference/profiler-relationship-info-enumeration.md)|Reprezentuje informacje o obiekcie w relacji. Używany w [strukturze PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_SCRIPT_TYPE, wyliczenie](../../winscript/reference/profiler-script-type-enumeration.md)|Określa typ skryptu.|  
  
|Struktury|Opis|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT, struktura](../../winscript/reference/profiler-heap-object-structure.md)|Reprezentuje obiekty sterty zebrane przez [metodę IActiveScriptProfilerControl3:: EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO, struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Reprezentuje opcjonalne informacje o obiektach sterty.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP, struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Reprezentuje relację obiektu sterty.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST, struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Reprezentuje listę relacji, które należą do obiektu sterty.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST, struktura](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Ta struktura jest skojarzona tylko z obiektami Functions. Lista zakresów reprezentuje zamknięcie funkcji jako listę zakresów, w których każdy zakres jest obiektem sterty ze skojarzoną listą właściwości, która reprezentuje zmienne w poszczególnych zakresach. W niektórych przypadkach nazwy obiektów w tym zakresie mogą nie być dostępne, tylko ich identyfikatory.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO, struktura](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Reprezentuje informacje o typie podciągu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)