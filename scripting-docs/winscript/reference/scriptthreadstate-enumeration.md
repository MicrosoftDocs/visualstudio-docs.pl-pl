---
title: Wyliczenie SCRIPTTHREADSTATE | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 906a309b25a1fe606fb37f8cbab70040e5a4c46f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157649"
---
# <a name="scriptthreadstate-enumeration"></a>Wyliczenie SCRIPTTHREADSTATE
Określa stan wątku w silnik wykonywania skryptów. To wyliczenie jest używane przez [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Określony wątek nie jest obsługi zdarzenia ze skryptem, tekst skryptu przetwarzania wykonywane od razu, lub nie jest uruchomiona makro skryptu.|  
|SCRIPTTHREADSTATE_RUNNING|Określony wątek jest aktywnie obsługi zdarzenia ze skryptem, tekst skryptu przetwarzania wykonywane od razu, lub uruchomienie skryptu makra.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, stałe i wyliczenia aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)