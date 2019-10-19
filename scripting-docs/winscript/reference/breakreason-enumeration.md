---
title: BREAKREASON, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572620"
---
# <a name="breakreason-enumeration"></a>Wyliczenie BREAKREASON
Wskazuje powód przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|BREAKREASON_STEP|Aparat języka jest w trybie taktowania.|  
|BREAKREASON_BREAKPOINT|Aparat języka napotkał jawny punkt przerwania.|  
|BREAKREASON_DEBUGGER_BLOCK|Aparat języka napotkał blok debugera w innym wątku.|  
|BREAKREASON_HOST_INITIATED|Host zażądał przerwania.|  
|BREAKREASON_LANGUAGE_INITIATED|Aparat języka zażądał przerwania.|  
|BREAKREASON_DEBUGGER_HALT|Środowisko IDE debugera zażądało przerwania.|  
|BREAKREASON_ERROR|Błąd wykonania spowodował przerwanie.|  
|BREAKREASON_JIT|Spowodowane uruchomieniem debugowania JIT.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)