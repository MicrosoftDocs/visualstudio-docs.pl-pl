---
title: IActiveScript::GetScriptThreadState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b191f1b70aa522cba0a04e0781ada69a8fe5ca5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097529"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Pobiera bieżący stan wątku skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stidThread`  
 [in] Identyfikator wątku, dla którego pożądany jest stan, lub jeden z następujących identyfikatorów specjalne wątku:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Podstawowy wątek; oznacza to wątek, w którym skryptów aparatu została utworzona.|  
|SCRIPTTHREADID_CURRENT|Aktualnie wykonywany wątek.|  
  
 `pstsState`  
 [out] Adres zmiennej, która otrzymuje stan wskazany wątku. Stan jest wskazywany przez jedno nazwane wartości stałe zdefiniowane przez [wyliczenie SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) wyliczenia. Jeśli ten parametr wskazuje bieżący wątek, stan może się zmienić w dowolnym momencie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany).|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może być wywołana z wątków-base bez skutkuje objaśnienia-base na obiektach hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)