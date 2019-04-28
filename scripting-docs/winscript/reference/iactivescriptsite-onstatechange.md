---
title: IActiveScriptSite::OnStateChange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad5719a93aec2940f1180a6ff45a028b937b0dfe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992535"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
Informuje hosta, że aparat skryptów zmienił Stany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ssScriptState`  
 [in] Wartość, która wskazuje nowy stan skryptu. Zobacz [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) metoda opis stanów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)