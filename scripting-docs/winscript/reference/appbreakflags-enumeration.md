---
title: Wyliczenie APPBREAKFLAGS | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0862e6fc670be6cd3d3ca9fbf67f453aa0772a90
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58158987"
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
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Aparat języka należy natychmiast przerywa, we wszystkich wątkach z BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Aparat języka należy natychmiast przerywa BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Aparat języka należy natychmiast przerywa w wątku przechodzenia krok po kroku z BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Aplikacja jest wykonanie zagnieżdżonych punkt przerwania.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Debuger jest przechodzenie krok po kroku na poziomie źródła.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Debuger jest przechodzenie krok po kroku na poziomie kodu bajtów.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Debuger jest przechodzenie krok po kroku na poziomie komputera.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maska wyprowadzenie się typy kroku.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Punkt przerwania jest w toku.|  
  
## <a name="remarks"></a>Uwagi  
 Niektóre flagi Określ, czy aparatów języka należy przerwać przy okazji dalej, podczas gdy inne flagi, Określanie trybu wykonywania krokowego debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON, wyliczenie](../../winscript/reference/breakreason-enumeration.md)