---
title: SCRIPTTHREADSTATE, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575654"
---
# <a name="scriptthreadstate-enumeration"></a>Wyliczenie SCRIPTTHREADSTATE
Określa stan wątku w aparacie skryptów. To wyliczenie jest używane przez metodę [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczeniowe  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Określony wątek nie obsługuje obecnie zdarzenia skryptowego, przetwarza natychmiast wykonanego skryptu lub uruchamia makro skryptu.|  
|SCRIPTTHREADSTATE_RUNNING|Określony wątek aktywnie obsługuje zdarzenia inicjowane przez skrypty, przetwarza bezpośrednio wykonywane skrypty lub uruchamiając makro skryptu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Kody błędów, stałe i wyliczenia aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)