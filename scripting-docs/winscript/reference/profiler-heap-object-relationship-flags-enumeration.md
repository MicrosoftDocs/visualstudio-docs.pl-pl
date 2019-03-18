---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS, wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 322f6f3352c1b0dfad4572d55e1ebe2388c8cc4a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58148168"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS — Wyliczenie
Flagi pokazujące, czy obiekt sterty wskazany w relacji obiektu jest metodę pobierającą czy ustawiającą. Używane w [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) metody, gdy wartość PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS jest określona w `enumFlags` parametru.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Ten obiekt stosu wskazany w relacji obiektu nie jest rozpoznawany jako metodę pobierającą czy ustawiającą.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Obiekt sterty wskazany w relacji obiektu to metoda pobierająca. Te informacje będą przechowywane w wysokich 2 bajtach (16 bitów) z [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) pola.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Obiekt sterty wskazany w relacji obiektu to metoda ustawiająca. Te informacje będą przechowywane w wysokich 2 bajtach (16 bitów) z `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` pola.|