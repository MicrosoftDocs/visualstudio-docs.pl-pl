---
title: IActiveScriptSite::OnScriptTerminate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f8ff7c3d531b46fa6681776e79fbb73f6d1efca2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087116"
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