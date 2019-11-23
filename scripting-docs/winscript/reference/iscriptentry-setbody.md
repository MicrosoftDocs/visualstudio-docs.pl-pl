---
title: 'IScriptEntry:: setbody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575381"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Ustawia tekst, który znajduje się w treści bloku skryptu `IScriptEntry` lub `IScriptScriptlet` Scriptlet.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 podczas Dla bloku skryptu `IScriptEntry` `psz` jest tekstem ujętym w Tagi skryptu.  
  
 Dla bloku funkcji `IScriptEntry` `psz` jest treścią funkcji.  
  
 Dla obiektu `IScriptScriptlet` (który pochodzi z `IScriptEntry`), `psz` jest tekstem skryptu Scriptlet.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry  interfejsu](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)