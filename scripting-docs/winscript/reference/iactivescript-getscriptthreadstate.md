---
title: 'IActiveScript:: GetScriptThreadState | Microsoft Docs'
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
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578006"
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
 podczas Identyfikator wątku, dla którego jest potrzebny stan, lub jeden z następujących identyfikatorów specjalnych wątków:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Wątek podstawowy; oznacza to, że wątek, w którym utworzono wystąpienie aparatu skryptów.|  
|SCRIPTTHREADID_CURRENT|Aktualnie wykonywany wątek.|  
  
 `pstsState`  
 określoną Adres zmiennej, która odbiera stan wskazanego wątku. Stan jest wskazywany przez jedną z nazwanych stałych określonych przez Wyliczenie [wyliczenia SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) . Jeśli ten parametr nie identyfikuje bieżącego wątku, stan może się zmienić w dowolnym momencie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może być wywoływana z wątków niebazowych bez wypełniania niepodstawowego wywołania obiektów hosta lub interfejsu [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)