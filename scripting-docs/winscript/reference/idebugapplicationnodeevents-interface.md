---
title: Interfejs IDebugApplicationNodeEvents | Microsoft Docs
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
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574716"
---
# <a name="idebugapplicationnodeevents-interface"></a>Interfejs IDebugApplicationNodeEvents
Udostępnia interfejs zdarzenia dla interfejsu `IDebugApplicationNode`.  
  
 Oprócz metod dziedziczonych z `IUnknown` interfejs `IDebugApplicationNodeEvents` udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Obsługuje zdarzenie po dodaniu węzła podrzędnego do obiektu węzła debugowania aplikacji.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Obsługuje zdarzenie po usunięciu węzła podrzędnego z obiektu węzła debugowania aplikacji.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Obsługuje zdarzenie oznaczające, że obiekt węzła aplikacji debugowania został odłączony od węzła nadrzędnego.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Obsługuje zdarzenie oznaczające, że obiekt węzła aplikacji debugowania został podłączony do węzła nadrzędnego.|  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)