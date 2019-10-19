---
title: APPBREAKFLAGS, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572665"
---
# <a name="appbreakflags-enumeration"></a>Wyliczenie APPBREAKFLAGS
Wskazuje bieżący stan debugowania aplikacji i wątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Aparat języka powinien natychmiast przerwać wszystkie wątki z BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Aparat języka powinien natychmiast przerwać od BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Aparat języka powinien natychmiast przerwać w wątku krokowe z BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Aplikacja znajduje się w zagnieżdżonym wykonaniu w punkcie przerwania.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Debuger działa na poziomie źródła.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Debuger działa na poziomie kodu bajtowego.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Debuger działa na poziomie komputera.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maska służąca do wykreślania typów kroków.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Punkt przerwania jest w toku.|  
  
## <a name="remarks"></a>Uwagi  
 Niektóre flagi określają, że aparaty języka mają być przerywane w następnej okazji, podczas gdy inne flagi określają tryb krokowe debugera.  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)    
 [BREAKREASON, wyliczenie](../../winscript/reference/breakreason-enumeration.md)