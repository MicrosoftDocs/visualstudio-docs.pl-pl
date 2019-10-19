---
title: 'IActiveScript:: GetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575737"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Pobiera bieżący stan aparatu obsługi skryptów. Ta metoda może być wywoływana z wątków niebazowych bez wypełniania niepodstawowego wywołania obiektów hosta lub interfejsu [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pss`  
 określoną Adres zmiennej, która otrzymuje wartość zdefiniowaną w wyliczeniu [wyliczenia SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) . Wartość wskazuje bieżący stan aparatu skryptów skojarzonego z wątkiem wywołującym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie, lub `E_POINTER`, jeśli określono nieprawidłowy wskaźnik.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)