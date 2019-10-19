---
title: 'IDebugApplicationNodeEvents:: OnAttach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e45af6b931dad28a41f8f4453db9fab96405df3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574691"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Obsługuje zdarzenie oznaczające, że obiekt węzła aplikacji debugowania został podłączony do węzła nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prddpParent`  
 podczas Węzeł aplikacji debugowania, który jest elementem nadrzędnym tego węzła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie oznaczające, że obiekt węzła aplikacji debugowania został podłączony do węzła nadrzędnego.  
  
 Realizatory interfejsu `IDebugApplicationNode` powodują podnoszenie tego zdarzenia.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationNodeEvents   interfejsu](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents:: onodłącz](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)    
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)