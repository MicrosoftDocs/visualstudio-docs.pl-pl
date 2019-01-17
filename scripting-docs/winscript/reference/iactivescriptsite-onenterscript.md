---
title: IActiveScriptSite::OnEnterScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ccef1b2bf63c4421843d3a33cab2e4f471a48251
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346517"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informuje hosta, że aparat skryptów rozpoczął wykonywanie kodu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Silnik wykonywania skryptów musi wywołać tej metody dla każdego wpisu lub wprowadzania do silnika wykonywania skryptów. Na przykład, jeśli skrypt wywołuje obiekt, który następnie uruchamia zdarzenie obsługiwane przez aparat skryptów aparatu skryptów należy wywołać `IActiveScriptSite::OnEnterScript` przed wykonaniem zdarzenia i musi wywołać [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) Metoda po wykonaniu zdarzenia, ale przed zwróceniem do obiektu, która wywołała zdarzenie. Mogą być zagnieżdżone wywołania tej metody. Każde wywołanie tej metody wymaga odpowiedniego wywołania `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)