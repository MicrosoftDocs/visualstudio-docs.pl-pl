---
title: 'IActiveScript:: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575797"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Klonuje bieżący aparat skryptów (minus dowolny bieżący stan wykonania), zwracając załadowany aparat skryptów, który nie ma lokacji w bieżącym wątku. Właściwości tego nowego aparatu skryptów będą takie same, jak w przypadku przejścia do stanu zainicjowania przy użyciu oryginalnego aparatu skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppscript`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu [IActiveScript](../../winscript/reference/iactivescript.md) sklonowanego aparatu skryptów. Host musi utworzyć lokację i wywołać metodę [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) w nowym aparacie skryptów, zanim będzie on znajdować się w stanie zainicjowania i dlatego można go użyć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład aparat skryptów nie został jeszcze załadowany lub zainicjowany).|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `IActiveScript::Clone` jest optymalizacją `IPersist*::Save`, `CoCreateInstance` i `IPersist*::Load`, więc stan nowego aparatu skryptów powinien być taki sam jak w przypadku zapisania i załadowania oryginalnego aparatu skryptów do nowego aparatu skryptów. Nazwane elementy są zduplikowane w aparacie sklonowanego skryptu, ale konkretne wskaźniki obiektów dla każdego elementu są zapomniane i są uzyskiwane przy użyciu metody [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) . Pozwala to na użycie identycznego modelu obiektów z punktami wejścia dla każdego wątku (modelem apartamentu).  
  
 Ta metoda jest używana w przypadku wielowątkowych hostów serwera, na których można uruchomić wiele wystąpień tego samego skryptu. Aparat obsługi skryptów może zwrócić `E_NOTIMPL`, w którym to przypadku host może osiągnąć ten sam wynik, duplikując stan trwały i tworząc nowe wystąpienie aparatu skryptów z interfejsem `IPersist*`.  
  
 Ta metoda może być wywoływana z wątków niebazowych bez wypełniania niepodstawowego wywołania obiektów hosta lub interfejsu [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)