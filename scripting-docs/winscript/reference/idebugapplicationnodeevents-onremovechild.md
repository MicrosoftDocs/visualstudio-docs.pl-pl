---
title: 'IDebugApplicationNodeEvents:: onRemoveChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onRemoveChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ff7b28f14c26029d64197ba919cc97c90a856c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574666"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Obsługuje zdarzenie po usunięciu węzła podrzędnego z obiektu węzła debugowania aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prddpChild`  
 podczas Węzeł aplikacji podrzędnej, który został usunięty.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie po usunięciu węzła podrzędnego z obiektu węzła debugowania aplikacji.  
  
 Realizatory interfejsu `IDebugApplicationNode` powodują podnoszenie tego zdarzenia.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationNodeEvents   interfejsu](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents:: onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)    
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)