---
title: PROFILER_HEAP_ENUM_FLAGS, wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d613ed3bcb4699f20d521f08b6c34d55d8363ba4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152788"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS — Wyliczenie
Flagi pokazujące, czy dodatkowe informacje o obiekcie sterty wskazanym w relacji obiektu jest widoczna. Używane w [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Ten obiekt stosu nie ujawnia dodatkowych informacji o relacji obiektu. Ten obiekt stosu zachowuje się w taki sam sposób jak [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Ten obiekt stosu ujawni informacje dotyczące tego, czy obiekt wskazany w relacji obiektu jest metodę pobierającą czy ustawiającą. Te informacje będą przechowywane w wysokich 2 bajtach (16 bitów) z [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) pola jako jeden z [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) wartości wyliczenia.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Ten obiekt stosu jest używana do poprawnego wyświetlania podciąg.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &AMP;#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Ten obiekt stosu jest używana do poprawnego wyświetlania podciąg.|