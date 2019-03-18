---
title: Struktura PROFILER_HEAP_OBJECT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1652c6ebffff88782ffcc879158a5142f22395d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151196"
---
# <a name="profilerheapobject-structure"></a>Struktura PROFILER_HEAP_OBJECT
Przedstawia obiekty sterty są zbierane przez [metoda IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|Identyfikator obiektu|[PROFILER_HEAP_OBJECT_ID, typ](../../winscript/reference/profiler-heap-object-id-type.md)|Identyfikator obiektu sterty.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS, typ](../../winscript/reference/profiler-external-object-address-type.md)|Adres obiektu zewnętrznego obiektu, takie jak obiektu przydzielone C++, które znajduje się poza sterty JavaScript.|  
|typeNameId|[PROFILER_HEAP_OBJECT_NAME_ID, typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Identyfikator nazwy typu obiektu sterty, pobierane z [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Tylko jeden z `externalObjectAddress` lub `typeName` znajduje się w zależności od `flags` wartość.|  
|flagi|[PROFILER_HEAP_OBJECT_FLAGS, wyliczenie](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flagi, zawierające podstawowe informacje o obiekcie sterty.|  
|optionalInfoCount|USHORT|Liczba [PROFILER_HEAP_OBJECT_OPTIONAL_INFO, struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md) rekordy, które są dostępne dla obiektu sterty.|