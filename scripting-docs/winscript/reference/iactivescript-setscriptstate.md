---
title: IActiveScript::SetScriptState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 58edef17fec1d94a09b327dff626658c42a273ba
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095033"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Umieszcza silnik wykonywania skryptów w danym stanie. Ta metoda może być wywołana z wątków-base bez skutkuje objaśnienia-base na obiektach hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ss`  
 [in] Ustawia silnik wykonywania skryptów w danym stanie. Może to być jedna z wartości zdefiniowanych w [wyliczenie SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_FAIL`|Aparat skryptów nie obsługuje przejścia z powrotem do stanu zainicjowania. Host należy odrzucić ten silnik wykonywania skryptów i tworzenie, inicjowanie i załadować nowy aparat skryptów, aby osiągnąć ten sam efekt.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany) i w związku z tym nie powiodła się.|  
|`OLESCRIPT_S_PENDING`|Metoda zostało pomyślnie dodane do kolejki, ale nie zmienił się stan jeszcze. Podczas zmiany stanu, witryna zostanie wywołany przez [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metody.|  
|`S_FALSE`|Wykonanie metody powiodło się, ale skryptu zostało już w danym stanie.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat stany aparatu obsługi skryptów, zobacz sekcję stany aparatu obsługi skryptów [aparatów skryptów Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)