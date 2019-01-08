---
title: Struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d0159dd50d57aa77a62dc3b8536b50712b96df5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087142"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>Struktura PROFILER_HEAP_OBJECT_OPTIONAL_INFO
Reprezentuje opcjonalne informacje o obiektach sterty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|typu informacji|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE, wyliczenie](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Typ informacje opcjonalne.|  
|Prototyp|[PROFILER_HEAP_OBJECT_ID, typ](../../winscript/reference/profiler-heap-object-id-type.md)|Identyfikator obiektu sterty prototypu obiektu.|  
|functionName|LPCWSTR|Nazwa funkcji obiekt sterty.|  
|elementAttributesSize|UINT|Rozmiar obiektu sterty atrybutów elementów.|  
|elementTextChildrenSize|UINT|Rozmiar obiektów podrzędnych tekstu obiektu sterty.|  
|Lista_zakresów|[PROFILER_HEAP_OBJECT_SCOPE_LIST, struktura](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Lista zakresów obiekt sterty.|  
|internalProperty|[PROFILER_HEAP_OBJECT_RELATIONSHIP, struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Właściwość wewnętrzna obiekt sterty.|  
|namePropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST, struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Lista właściwości name obiektu sterty.|  
|indexPropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST, struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Lista właściwości indeksu obiekt sterty.|  
|relationshipList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST, struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Lista relacje między obiektami sterty.|  
|eventList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST, struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Lista zdarzeń obiekt sterty.|