---
title: Struktura PROFILER_HEAP_OBJECT_SCOPE_LIST | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1285e4efa3db8a7ec99808f5888d3dbf948e589
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152525"
---
# <a name="profilerheapobjectscopelist-structure"></a>Struktura PROFILER_HEAP_OBJECT_SCOPE_LIST
Ta struktura jest skojarzony z tylko obiekty funkcyjne. Lista zakresów reprezentuje zamknięcia dla funkcji jako listę zakresów, gdzie każdy zakres jest obiekt sterty przy użyciu listy skojarzonej właściwości reprezentujący zmienne w każdej z danego zakresu. W niektórych przypadkach nazwy obiektów w zakresie będą niedostępne i ich Indeksuj tylko do listy właściwości jest dostępna.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|count|UINT|Liczba zakresów|  
|scopes|[PROFILER_HEAP_OBJECT_ID, typ](../../winscript/reference/profiler-heap-object-id-type.md)|Tablica zakresów.|