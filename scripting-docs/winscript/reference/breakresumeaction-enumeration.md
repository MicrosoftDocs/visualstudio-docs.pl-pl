---
title: Wyliczenie BREAKRESUMEACTION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5c79aacc64eb57282bf09f7e4673980396b37ea
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58154650"
---
# <a name="breakresumeaction-enumeration"></a>Wyliczenie BREAKRESUMEACTION
W tym artykule opisano sposoby kontynuowało działanie od punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Przerywa aplikacji.|  
|BREAKRESUMEACTION_CONTINUE|Będzie kontynuował działanie.|  
|BREAKRESUMEACTION_STEP_INTO|Kroki opisane w procedurze.|  
|BREAKRESUMEACTION_STEP_OVER|Przeprowadza użytkownika przez procedurę.|  
|BREAKRESUMEACTION_STEP_OUT|Kroki poza bieżącą procedurę.|  
|BREAKRESUMEACTION_IGNORE|Przechodzi do stanu.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Kroki, aby następny dokument.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)