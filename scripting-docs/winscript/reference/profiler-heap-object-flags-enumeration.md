---
title: Wyliczenie PROFILER_HEAP_OBJECT_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7fde5ed275691d78e534cd7b8d8e958a8f20325
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823842"
---
# <a name="profilerheapobjectflags-enumeration"></a>Wyliczenie PROFILER_HEAP_OBJECT_FLAGS
Flagi, które reprezentują podstawowe informacje o obiekcie sterty. Używane w [struktura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|Ten obiekt stosu została przydzielona po poprzednie żądanie wyliczenia sterty. [Typ PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md) wartości mogą być ponownie używane, jeśli obiekt są zbierane.|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|Ten obiekt stosu jest obiektem głównym wykresu obiektu.|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|Ten obiekt stosu jest z witryny skryptu, który został zamknięty.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|Ten obiekt stosu została przydzielona poza stercie JavaScript wyrzucania elementów bezużytecznych.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|Ten obiekt stosu został przydzielony w stercie wyrzucania elementów bezużytecznych i implementuje IUnknown poza.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|Ten obiekt stosu została przydzielona poza stercie wyrzucania elementów bezużytecznych i implementuje interfejs IDISPATCH.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|Rozmiar ten obiekt stosu jest przybliżona.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|Rozmiar ten obiekt stosu jest niedostępna.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|Stos, obiekt jest wystąpieniem środowiska wykonawczego Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|Obiekt sterty jest klasy środowiska wykonawczego Windows Runtime.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|Obiekt sterty jest delegat środowiska wykonawczego Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|Obiekt sterty znajduje się w przestrzeni nazw środowiska wykonawczego Windows.|