---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db8683534e449b2cdd8fcdb344c245d93da8fafc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58144670"
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