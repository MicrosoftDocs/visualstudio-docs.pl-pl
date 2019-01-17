---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a451f4883373978772643e11fe22feb9122be30e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349754"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Pobiera ciąg zdefiniowany przez hosta, który unikatowo identyfikuje bieżącej wersji dokumentu. Jeśli powiązany dokument został zmieniony poza zakresem skrypt Windows (tak jak w przypadku edytowany przy użyciu programu Notepad strony HTML), aparat skryptów zapisać to wraz z jego utrwalonego stanu wymuszania ponownej kompilacji podczas następnego załadowaniu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrVersionString`  
 [out] Adres ciąg wersji dokumentów zdefiniowanych przez hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_NOTIMPL` Jeśli ta metoda nie jest obsługiwana.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `E_NOTIMPL` ma zostać zwrócona, aparat skryptów należy przyjąć, że skrypt jest zsynchronizowany z dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)