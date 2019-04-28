---
title: Wyliczenie PROFILER_RELATIONSHIP_INFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aa0a94668d06f75b959de2ee933ab079feba596
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808896"
---
# <a name="profilerrelationshipinfo-enumeration"></a>Wyliczenie PROFILER_RELATIONSHIP_INFO
Reprezentuje informacje dotyczące obiektu w relacji. Używane w [struktura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|Obiekt jest liczbą.|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|Obiekt jest ciąg.|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|Obiekt jest obiektem sterty.|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04|Obiekt zewnętrzny, oznacza to, że nie jest na stercie wyrzucania elementów bezużytecznych.|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|Obiekt jest ciąg BSTR.|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|Obiekt jest PODCIĄGIEM.|