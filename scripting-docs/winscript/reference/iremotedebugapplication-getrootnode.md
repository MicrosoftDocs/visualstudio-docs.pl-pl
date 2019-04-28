---
title: IRemoteDebugApplication::GetRootNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetRootNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetRootNode
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef8337e27bb5a666e8d5d8d38abcafb044da02ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944222"
---
# <a name="iremotedebugapplicationgetrootnode"></a>IRemoteDebugApplication::GetRootNode
Zwracanie węzła aplikacji w ramach której są dodawane wszystkie węzły, powiązane z daną aplikacją.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppdanRoot`  
 [out] Węzeł aplikacji debugowania, w ramach której są dodawane wszystkie węzły, powiązane z daną aplikacją.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca węzła aplikacji w ramach której są dodawane wszystkie węzły, powiązane z daną aplikacją.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplication, interfejs](../../winscript/reference/iremotedebugapplication-interface.md)