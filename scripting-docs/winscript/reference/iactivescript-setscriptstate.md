---
title: 'IActiveScript:: SetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577992"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Umieszcza aparat wykonywania skryptów w danym stanie. Ta metoda może być wywoływana z wątków niebazowych bez wypełniania niepodstawowego wywołania obiektów hosta lub interfejsu [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ss`  
 podczas Ustawia aparat wykonywania skryptów dla danego stanu. Może być jedną z wartości zdefiniowanych w wyliczeniu [wyliczenia SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_FAIL`|Aparat skryptów nie obsługuje przejścia z powrotem do stanu zainicjowania. Host musi odrzucić ten aparat skryptów i utworzyć, zainicjować i załadować nowy aparat obsługi skryptów, aby osiągnąć ten sam efekt.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany) i w związku z tym nie powiodło się.|  
|`OLESCRIPT_S_PENDING`|Metoda została pomyślnie umieszczona w kolejce, ale stan nie został jeszcze zmieniony. Po zmianie stanu lokacja zostanie wywołana z powrotem przez metodę [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Metoda zakończyła się pomyślnie, ale skrypt już znajduje się w danym stanie.|  
  
## <a name="remarks"></a>Uwagi  
 Więcej informacji o Stanach aparatu skryptów znajduje się w sekcji Stany aparatu skryptów w [aparatach skryptów systemu Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)    
 [IActiveScript:: GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)    
 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)    
 [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)