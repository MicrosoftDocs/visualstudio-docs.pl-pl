---
title: IEnumRemoteDebugApplicationThreads::Clone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Clone
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Clone
ms.assetid: d016e7cf-ae73-48ff-aee7-810222e0b05c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12a6b7ccd34d0086314b1709ad7cc76bfdef6dbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807228"
---
# <a name="ienumremotedebugapplicationthreadsclone"></a>IEnumRemoteDebugApplicationThreads::Clone
Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Clone(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pperdat`  
 [out] Zwraca `IEnumRemoteDebugApplicationThreads` interfejsu klonu modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumRemoteDebugApplicationThreads, interfejs](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)