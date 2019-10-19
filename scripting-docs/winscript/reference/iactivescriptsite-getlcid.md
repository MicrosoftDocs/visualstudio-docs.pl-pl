---
title: 'IActiveScriptSite:: GetLcid | Microsoft Docs'
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
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570740"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Pobiera identyfikator ustawień regionalnych skojarzony z interfejsem użytkownika hosta. Aparat skryptów używa identyfikatora, aby upewnić się, że ciągi błędów i inne elementy interfejsu użytkownika wygenerowane przez aparat pojawiają się w odpowiednim języku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `plcid`  
 określoną Adres zmiennej, która otrzymuje identyfikator ustawień regionalnych dla elementów interfejsu użytkownika wyświetlanych przez aparat skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_NOTIMPL`|Ta metoda nie jest zaimplementowana. Użyj zdefiniowanych przez system ustawień regionalnych.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta metoda zwróci `E_NOTIMPL`, należy użyć identyfikatora ustawień regionalnych zdefiniowanych przez system.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)