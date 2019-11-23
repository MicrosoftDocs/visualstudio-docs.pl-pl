---
title: 'IDebugApplicationNodeEvents:: onodłącz | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onDetach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onDetach
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1a33cbec8ef032c1c4fedba28ad4013e676f0d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574678"
---
# <a name="idebugapplicationnodeeventsondetach"></a>IDebugApplicationNodeEvents::onDetach
Obsługuje zdarzenie oznaczające, że obiekt węzła aplikacji debugowania został odłączony od węzła nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onDetach();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie oznaczające, że obiekt węzła aplikacji debugowania został odłączony od węzła nadrzędnego.  
  
 Realizatory interfejsu `IDebugApplicationNode` powodują podnoszenie tego zdarzenia.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationNodeEvents  interfejsu](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents:: OnAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)   
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)