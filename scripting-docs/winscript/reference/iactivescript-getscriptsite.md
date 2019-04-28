---
title: IActiveScript::GetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b57c4282b7ec77eb4af2ffa983479ae77388e1c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935774"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Pobiera obiekt lokacji skojarzone z aparatu skryptów Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator żądanego interfejsu.  
  
 `ppvSiteObject`  
 [out] Adres lokalizacji, która otrzymuje wskaźnik interfejsu do obiektu witryny hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_NOINTERFACE`|Wybrany interfejs nie jest obsługiwana.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`S_FALSE`|Lokacja nie została ustawiona; `ppvSiteObject` parametr ma wartość `NULL`.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)