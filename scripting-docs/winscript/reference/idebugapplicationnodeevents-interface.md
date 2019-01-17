---
title: Interfejs IDebugApplicationNodeEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0396ed90437a98c8ee398f3c3acb0aeb5ddc77e2
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348415"
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