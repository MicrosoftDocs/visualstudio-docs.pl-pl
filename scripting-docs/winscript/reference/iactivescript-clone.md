---
title: IActiveScript::Clone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 084da486d2e5831176130ccd080b9e09a80c9bcc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093668"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Klony bieżącym silnikiem skryptującym (bez żadnych bieżący stan wykonania), zwracając załadować aparat skryptów, który ma żadna lokacja w bieżącym wątku. Właściwości tego nowego aparatu skryptów będzie taka sama jak właściwości, które oryginalny aparat skryptu będą miały, jeżeli były przenoszone do stanu zainicjowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppscript`  
 [out] Adres zmiennej, która otrzymuje wskaźnik [IActiveScript](../../winscript/reference/iactivescript.md) interfejsu sklonowany silnik wykonywania skryptów. Host musi utworzyć witryny i wywołania [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) metody na nowy silnik wykonywania skryptów, zanim będzie on w stanie inicjowania i w związku z tym, można używać.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparat skryptów jeszcze nie został załadowany lub zainicjowany).|  
  
## <a name="remarks"></a>Uwagi  
 `IActiveScript::Clone` Metodą jest optymalizacja `IPersist*::Save`, `CoCreateInstance`, i `IPersist*::Load`, więc stan aparat skryptów powinna być taka sama, tak, jakby stan oryginalny aparat skryptu zostały zapisane i ładowane do nowego aparatu obsługi skryptów. Nazwanych elementów są duplikowane w sklonowanym silnik wykonywania skryptów, ale konkretny obiekt dla każdego elementu są zapomniane i są pobierane z [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metody. Dzięki temu model obiektowy identyczne punkty wejścia na wątek (modelu typu apartment) ma być używany.  
  
 Ta metoda jest używana dla hostów serwera wielowątkowych, które można uruchomić wiele wystąpień tego samego skryptu. Aparat skryptów mogą zwracać `E_NOTIMPL`, w którym to przypadku hosta można osiągnąć ten sam wynik duplikowania trwały stan i tworząc nowe wystąpienie aparatu skryptów za pomocą `IPersist*` interfejsu.  
  
 Ta metoda może być wywołana z wątków-base bez skutkuje objaśnienia-base na obiektach hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)