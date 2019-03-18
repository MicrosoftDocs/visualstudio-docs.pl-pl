---
title: IActiveScriptSite::OnLeaveScript | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: da39058a8f069c4799835108372d11849d86444e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160748"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informuje hosta, że wykonywanie kodu skryptu zwróciło silnik wykonywania skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów musi wywołać tę metodę przed zwróceniem sterowania do aplikacji wywołującej, który wprowadzono silnik wykonywania skryptów. Na przykład, jeśli skrypt wywołuje obiekt, który następnie uruchamia zdarzenie obsługiwane przez aparat skryptów aparatu skryptów należy wywołać [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) metoda przed wykonaniem zdarzeń, a musi wywołać `IActiveScriptSite::OnLeaveScript`po wykonaniu zdarzenia przed zwróceniem do obiektu, która wywołała zdarzenie. Mogą być zagnieżdżone wywołania tej metody. Każde wywołanie `IActiveScriptSite::OnEnterScript` wymaga odpowiedniego wywołania tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)