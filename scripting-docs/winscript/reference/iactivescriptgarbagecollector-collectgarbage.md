---
title: IActiveScriptGarbageCollector::CollectGarbage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 478a7a39c69e0c2106e3c6cc308f44f8f7aa3201
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097126"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Host skryptów aktywnych wywołuje tę metodę można uruchomić wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptgctype`  
 [in] [Wyliczenie SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) określająca, czy ma być normalne lub pełnego wyrzucania elementów bezużytecznych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptGarbageCollector, interfejs](../../winscript/reference/iactivescriptgarbagecollector-interface.md)