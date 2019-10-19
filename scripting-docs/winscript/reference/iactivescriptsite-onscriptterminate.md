---
title: 'IActiveScriptSite:: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570203"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informuje hosta o ukończeniu wykonywania skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarResult`  
 podczas Adres zmiennej zawierającej wynik skryptu lub `NULL`, jeśli skrypt nie wygenerował żadnego wyniku.  
  
 `pexcepinfo`  
 podczas Adres struktury `EXCEPINFO`, która zawiera informacje o wyjątku wygenerowane po przerwaniu działania skryptu lub `NULL`, jeśli żaden wyjątek nie został wygenerowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów wywołuje tę metodę przed wywołaniem metody [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) z ustawioną flagą SCRIPTSTATE_INITIALIZED. Ta metoda może służyć do powrotu stanu ukończenia i wyników do hosta. Należy zauważyć, że wiele języków skryptów, które są oparte na zdarzeniach ujścia z hosta, mają zakresy życiowe, które są definiowane przez hosta. W takim przypadku ta metoda może nigdy nie zostać wywołana.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)