---
title: Wyliczenie BREAKREASON | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955411"
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
|BREAKREASON_STEP|Aparat języka jest w trybie wykonywania krokowego.|  
|BREAKREASON_BREAKPOINT|Aparat języka napotkał jawne punktu przerwania.|  
|BREAKREASON_DEBUGGER_BLOCK|Aparat języka napotkał bloku debugera na inny wątek.|  
|BREAKREASON_HOST_INITIATED|Host zażądał przerwania.|  
|BREAKREASON_LANGUAGE_INITIATED|Aparat języka zażądał przerwania.|  
|BREAKREASON_DEBUGGER_HALT|Debuger IDE zażądał podziału.|  
|BREAKREASON_ERROR|Błąd wykonywania spowodował przerwanie.|  
|BREAKREASON_JIT|Przyczyną uruchamiania debugowanie JIT.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)