---
title: 'IActiveScript:: SetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575327"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informuje aparat obsługi skryptów w witrynie interfejsu [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) dostarczonej przez hosta. Wywołaj tę metodę przed użyciem innych metod interfejsu [IActiveScript](../../winscript/reference/iactivescript.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pScriptSite`  
 podczas Adres witryny skryptu dostarczonej przez hosta, która ma zostać skojarzona z tym wystąpieniem aparatu skryptów. Lokacja musi być unikatowo przypisana do tego wystąpienia aparatu skryptów; nie może być współużytkowana z innymi aparatami skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_FAIL`|Wystąpił nieokreślony błąd; aparat skryptów nie mógł zakończyć inicjowania lokacji.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Wywołanie nie było oczekiwane (na przykład witryna została już ustawiona).|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)