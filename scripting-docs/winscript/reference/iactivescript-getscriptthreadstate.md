---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a0066894830c111a8e0ad18f7acdc09d6114162e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935613"
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