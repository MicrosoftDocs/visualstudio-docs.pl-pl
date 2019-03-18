---
title: Wyliczenie BREAKPOINT_STATE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: faca5ef7bc89bc16d646f66fb897f1dc44eb831a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58154676"
---
# <a name="breakpointstate-enumeration"></a>Wyliczenie BREAKPOINT_STATE
Wskazuje stan punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|BREAKPOINT_DELETED|Punkt przerwania już nie istnieje, ale nadal istnieją odwołania do niego.|  
|BREAKPOINT_DISABLED|Punkt przerwania istnieje, ale jest wyłączona.|  
|BREAKPOINT_ENABLED|Punkt przerwania istnieje i jest włączona.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)