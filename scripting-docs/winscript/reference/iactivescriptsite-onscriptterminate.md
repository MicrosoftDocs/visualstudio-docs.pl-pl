---
title: IActiveScriptSite::OnScriptTerminate | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 664f974b26a2cae0d1e16d37dc3bc66e95993d6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992656"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informuje hosta, że skrypt zakończy działanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarResult`  
 [in] Adres zmiennej, który zawiera wynik skryptu lub `NULL` skrypt utworzony żadnego wyniku.  
  
 `pexcepinfo`  
 [in] Adres `EXCEPINFO` strukturę, która zawiera informacje o wyjątku generowane, gdy skrypt zakończony, lub `NULL` Jeśli wyjątek nie został wygenerowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów wywołuje tę metodę, przed wywołaniem do [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metoda z ustawioną flagą SCRIPTSTATE_INITIALIZED, zostanie zakończona. Ta metoda może służyć do zwrócenia stanu ukończenia i wyników do hosta. Należy zauważyć, że wiele języków skryptów, które są oparte na wychwytywania zdarzeń z hosta, zakresy życia, które są zdefiniowane przez hosta. W takim przypadku ta metoda nie może zostać wywołana.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)