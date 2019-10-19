---
title: 'IActiveScriptSite:: OnEnterScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570360"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informuje hosta o tym, że aparat obsługi skryptów rozpoczął wykonywanie kodu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie.  
  
## <a name="remarks"></a>Uwagi  
 Aparat obsługi skryptów musi wywołać tę metodę przy każdym wpisie lub odpisaniu do aparatu skryptów. Jeśli na przykład skrypt wywołuje obiekt, który uruchamia zdarzenie obsługiwane przez aparat skryptów, aparat obsługi skryptów musi wywołać `IActiveScriptSite::OnEnterScript` przed wykonaniem zdarzenia i musi wywołać metodę [IActiveScriptSite:: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) po wykonaniu zdarzenia ale przed powrotem do obiektu, który wygenerował zdarzenie. Wywołania tej metody mogą być zagnieżdżane. Każde wywołanie tej metody wymaga wywołania odpowiadającego `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)