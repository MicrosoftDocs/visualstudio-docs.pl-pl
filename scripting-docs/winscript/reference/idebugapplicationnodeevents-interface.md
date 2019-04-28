---
title: Interfejs IDebugApplicationNodeEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7412e258c7f67f44bde6f69b593a1eecb1d84e07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822278"
---
# <a name="idebugapplicationnodeevents-interface"></a>Interfejs IDebugApplicationNodeEvents
Udostępnia interfejs zdarzenia dla `IDebugApplicationNode` interfejsu.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugApplicationNodeEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Obsługuje zdarzenie, gdy węzeł podrzędny zostanie dodany do obiektu węzła debugowania aplikacji.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Obsługuje zdarzenie, gdy węzeł podrzędny zostanie usunięty z obiektu węzła debugowania aplikacji.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Obsługuje zdarzenie, co oznacza, że obiekt węzła debugowania aplikacji została odłączona od węzła nadrzędnego.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Obsługuje zdarzenie, co oznacza, że obiekt węzła debugowania aplikacji został dołączony do węzła nadrzędnego.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)