---
title: 'IActiveScriptSite:: GetDocVersionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571131"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Pobiera ciąg zdefiniowany przez hosta, który jednoznacznie identyfikuje bieżącą wersję dokumentu. Jeśli powiązany dokument został zmieniony poza zakresem skryptu systemu Windows (tak jak w przypadku strony HTML edytowanej przy użyciu Notatnika), aparat obsługi skryptów może je zapisać wraz z trwałym stanem, wymuszając ponowną kompilację przy następnym załadowaniu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrVersionString`  
 określoną Adres ciągu wersji dokumentu zdefiniowanego przez hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie, lub `E_NOTIMPL`, jeśli ta metoda nie jest obsługiwana.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `E_NOTIMPL` jest zwracana, aparat skryptów powinien założyć, że skrypt jest zsynchronizowany z dokumentem.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)