---
title: BREAKRESUMEACTION, Wyliczenie | Microsoft Docs
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
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572608"
---
# <a name="breakresumeaction-enumeration"></a>Wyliczenie BREAKRESUMEACTION
Opisuje sposoby kontynuowania pracy z punktu przerwania.  
  
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
|BREAKRESUMEACTION_ABORT|Przerywa działanie aplikacji.|  
|BREAKRESUMEACTION_CONTINUE|Kontynuuje działanie.|  
|BREAKRESUMEACTION_STEP_INTO|Kroki do procedury.|  
|BREAKRESUMEACTION_STEP_OVER|Kroki procedury.|  
|BREAKRESUMEACTION_STEP_OUT|Kroki z bieżącej procedury.|  
|BREAKRESUMEACTION_IGNORE|Kontynuuje działanie ze stanem.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Kroki do następnego dokumentu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)