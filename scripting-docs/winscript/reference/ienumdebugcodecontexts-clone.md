---
title: IEnumDebugCodeContexts::Clone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Clone
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Clone
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a08c65a7be5ed0b6394ef5e0aab284a03a52a240
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951450"
---
# <a name="ienumdebugcodecontextsclone"></a>IEnumDebugCodeContexts::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppescc`  
 [out] Zwraca `IEnumDebugCodeContexts` interfejsu klonu modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugCodeContexts, interfejs](../../winscript/reference/ienumdebugcodecontexts-interface.md)