---
title: IActiveScript::SetScriptSite | Microsoft Docs
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
ms.openlocfilehash: 3fdf5f3ae84d1a991d67170b5f2b02114b91ee05
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157071"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informuje silnik wykonywania skryptów z [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) lokacji interfejsu udostępniane przez hosta. Wywołanie tej metody przed wszystkimi pozostałymi [IActiveScript](../../winscript/reference/iactivescript.md) służy metod interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pScriptSite`  
 [in] Adres witryny dostarczony host skrypt ma zostać skojarzony z tym wystąpieniem silnik wykonywania skryptów. Lokacji należy jednoznacznie przypisać do tego wystąpienia aparatu skryptów; Nie można udostępnić z innych aparatów obsługi skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_FAIL`|Wystąpił nieokreślony błąd; aparat skryptów nie może zakończyć inicjowanie lokacji.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład lokacji został już ustawiony).|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)