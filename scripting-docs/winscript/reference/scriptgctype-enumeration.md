---
title: Wyliczenie SCRIPTGCTYPE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a5de3ea949203ad7a6dca0ea777fdbc9514ba6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840242"
---
# <a name="scriptgctype-enumeration"></a>Wyliczenie SCRIPTGCTYPE
Typ wyrzucania elementów bezużytecznych do wykonania. Używane w [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Wyrzucanie elementów bezużytecznych normalny. Wartość całkowita wynosi 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Wyrzucanie elementów bezużytecznych wyczerpujący. Wartość liczby całkowitej to 1.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kody błędów, stałe i wyliczenia aktywnego skryptu](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)