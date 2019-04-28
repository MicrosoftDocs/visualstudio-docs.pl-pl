---
title: IDebugApplicationNode::Detach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Detach
ms.assetid: 36bb3e54-a4df-48d5-a6de-3b8d4c0e98a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce6f4fdf0e5c49062f0d930b64de8fb1b06888d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990354"
---
# <a name="idebugapplicationnodedetach"></a>IDebugApplicationNode::Detach
Usuwa ten węzeł aplikacji z drzewa projektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda usuwa ten węzeł aplikacji z drzewa projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)   
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)