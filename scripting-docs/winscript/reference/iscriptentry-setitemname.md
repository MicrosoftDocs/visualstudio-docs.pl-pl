---
title: 'IScriptEntry:: setitemname | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575371"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Ustawia nazwę elementu, który identyfikuje obiekt `IScriptEntry`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 podczas Adres buforu, który zawiera nazwę elementu. Nazwa elementu jest używana przez hosta do identyfikowania wpisu.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie powiodła się.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku obiektów `IScriptEntry` ta metoda zwraca `S_OK`.  
  
 W przypadku obiektów `IScriptScriptlet` (które pochodzą z `IScriptEntry`) Metoda ta zwraca `E_FAIL`. Dla `IScriptScriptlet` obiektów nazwa elementu jest ustawiana przez [IActiveScriptAuthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) i nie można jej zmienić.  
  
## <a name="see-also"></a>Zobacz także  
 [IScriptEntry  interfejsu](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)