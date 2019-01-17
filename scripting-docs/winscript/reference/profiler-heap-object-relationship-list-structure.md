---
title: Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cfbd2f3924391a8c7ff75ea5e4c06e7b0f07c35
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349070"
---
# <a name="profilerheapobjectrelationshiplist-structure"></a>Struktura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST
Reprezentuje listę relacje, które należą do obiekt sterty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|count|UINT|Liczba relacji obiekt sterty.|  
|elementy|[PROFILER_HEAP_OBJECT_RELATIONSHIP, struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Relacje obiekt sterty.|