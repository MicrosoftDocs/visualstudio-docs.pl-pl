---
title: IActiveScriptSite::GetLCID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6ebcfec9764aae98f7d74ac98e0c88ecec7c4da
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155514"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Pobiera identyfikator ustawień regionalnych skojarzoną z interfejsem użytkownika hosta. Aparat skryptów używa identyfikatora, aby upewnić się, że ciągi błędów i inne elementy interfejsu użytkownika, generowane przez aparat są wyświetlane w odpowiednim języku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `plcid`  
 [out] Adres zmiennej, która odbiera identyfikator ustawień regionalnych dla elementów interfejsu użytkownika wyświetlany przez silnik wykonywania skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_NOTIMPL`|Ta metoda nie jest zaimplementowana. Użyj ustawienia regionalne zdefiniowane przez system.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zwraca `E_NOTIMPL`, zdefiniowaną przez system identyfikator ustawień regionalnych, które powinny być używane.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)