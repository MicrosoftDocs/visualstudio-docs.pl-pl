---
title: IActiveScript::GetScriptState | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0f9f3bedee9af9ae3cb145108d801f252267d5d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935751"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Pobiera bieżący stan silnika wykonywania skryptów. Ta metoda może być wywołana z wątków-base bez skutkuje objaśnienia-base na obiektach hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pss`  
 [out] Adres zmiennej, który otrzymuje wartość zdefiniowana w [wyliczenie SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) wyliczenia. Wartość wskazuje bieżący stan skojarzony wątek wywołujący silnik wykonywania skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_POINTER` Jeśli określono nieprawidłowy wskaźnik.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)