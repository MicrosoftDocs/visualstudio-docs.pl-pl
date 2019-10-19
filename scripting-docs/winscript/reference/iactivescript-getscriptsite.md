---
title: 'IActiveScript:: GetScriptSite | Microsoft Docs'
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
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575744"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Pobiera obiekt lokacji skojarzony z aparatem skryptów systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 podczas Identyfikator żądanego interfejsu.  
  
 `ppvSiteObject`  
 określoną Adres lokalizacji, która otrzymuje wskaźnik interfejsu do obiektu lokacji hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_NOINTERFACE`|Określony interfejs nie jest obsługiwany.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`S_FALSE`|Nie ustawiono lokacji; parametr `ppvSiteObject` jest ustawiony na `NULL`.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScript](../../winscript/reference/iactivescript.md)