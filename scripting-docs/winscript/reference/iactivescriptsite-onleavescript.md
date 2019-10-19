---
title: 'IActiveScriptSite:: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570319"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informuje hosta, że aparat obsługi skryptów zwrócił kod skryptu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie.  
  
## <a name="remarks"></a>Uwagi  
 Aparat obsługi skryptów musi wywołać tę metodę przed zwróceniem kontroli do aplikacji wywołującej, która została wprowadzona do aparatu wykonywania skryptów. Jeśli na przykład skrypt wywołuje obiekt, który uruchamia zdarzenie obsługiwane przez aparat skryptów, aparat obsługi skryptów musi wywołać metodę [IActiveScriptSite:: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) przed wykonaniem zdarzenia i musi wywołać `IActiveScriptSite::OnLeaveScript` po wykonaniu zdarzenia. przed zwróceniem do obiektu, który wygenerował zdarzenie. Wywołania tej metody mogą być zagnieżdżane. Każde wywołanie do `IActiveScriptSite::OnEnterScript` wymaga odpowiedniego wywołania do tej metody.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)