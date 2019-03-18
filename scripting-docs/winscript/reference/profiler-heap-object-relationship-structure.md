---
title: Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a905a44f2ef686181c5a859699277d16f6cd374
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58153022"
---
# <a name="profilerheapobjectrelationship-structure"></a>Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP
Reprezentuje relację obiekt sterty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP{    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;    PROFILER_RELATIONSHIP_INFO relationshipInfo;    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union    {        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|relationshipId|[PROFILER_HEAP_OBJECT_NAME_ID, typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identyfikator relacji z nazwę [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[PROFILER_RELATIONSHIP_INFO, wyliczenie](../../winscript/reference/profiler-relationship-info-enumeration.md)|Informacje na temat relacji.|  
|numberValue|double|Wartość liczbowa. Tylko jeden z `numberValue` / `stringValue` / `objectId` / `externalObjectAddress` jest ustawiona, na podstawie `relationshipInfo` wartości.|  
|stringValue|LPCWSTR|Wartość ciągu.|  
|Identyfikator obiektu|[PROFILER_HEAP_OBJECT_ID, typ](../../winscript/reference/profiler-heap-object-id-type.md)|Identyfikator obiektu sterty.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS, typ](../../winscript/reference/profiler-external-object-address-type.md)|Adres obiektu zewnętrznego.|  
|Podciąg|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO, struktura](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Informacje o typie podciąg.|