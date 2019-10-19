---
title: 'IActiveScriptGarbageCollector:: Odzyskaj pamięć | Microsoft Docs'
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
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573582"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Host aktywnego skryptu wywołuje tę metodę, aby rozpocząć odzyskiwanie pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptgctype`  
 podczas [Wyliczenie SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) , które określa, czy wykonywać normalne czy wyczerpujące odzyskiwanie pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptGarbageCollector, interfejs](../../winscript/reference/iactivescriptgarbagecollector-interface.md)