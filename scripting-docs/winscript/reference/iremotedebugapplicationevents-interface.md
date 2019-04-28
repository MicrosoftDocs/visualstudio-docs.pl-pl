---
title: IRemoteDebugApplicationEvents Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEvents interface
ms.assetid: 9626519e-910c-48e0-ae99-c711ce6628fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052a408d6e92066c14617f46f722d3e603985195
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943809"
---
# <a name="iremotedebugapplicationevents-interface"></a>Interfejs IRemoteDebugApplicationEvents
`IRemoteDebugApplicationEvents` Interfejs jest interfejs zdarzenia dostarczone przez aplikację do debugowania. Ten interfejs jest zawsze wywoływana z wewnątrz wątku debugera.  
  
 Oprócz metod odziedziczone `IUnknown`, `IRemoteDebugApplicationEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IRemoteDebugApplicationEvents::OnConnectDebugger](../../winscript/reference/iremotedebugapplicationevents-onconnectdebugger.md)|Wydarzenie connect uchwytów w debugerze.|  
|[IRemoteDebugApplicationEvents::OnDisconnectDebugger](../../winscript/reference/iremotedebugapplicationevents-ondisconnectdebugger.md)|Uchwyty, a debuger zdarzenia rozłączenia.|  
|[IRemoteDebugApplicationEvents::OnSetName](../../winscript/reference/iremotedebugapplicationevents-onsetname.md)|Obsługuje zdarzenie nazwę zestawu.|  
|[IRemoteDebugApplicationEvents::OnDebugOutput](../../winscript/reference/iremotedebugapplicationevents-ondebugoutput.md)|Obsługuje zdarzenie danych wyjściowych debugera.|  
|[IRemoteDebugApplicationEvents::OnClose](../../winscript/reference/iremotedebugapplicationevents-onclose.md)|Obsługuje zdarzenie zamknięcia aplikacji.|  
|[IRemoteDebugApplicationEvents::OnEnterBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onenterbreakpoint.md)|Obsługuje zdarzenie do wprowadzania punktu przerwania.|  
|[IRemoteDebugApplicationEvents::OnLeaveBreakPoint](../../winscript/reference/iremotedebugapplicationevents-onleavebreakpoint.md)|Obsługuje zdarzenie opuszczania punktu przerwania.|  
|[IRemoteDebugApplicationEvents::OnCreateThread](../../winscript/reference/iremotedebugapplicationevents-oncreatethread.md)|Obsługuje tworzenie zdarzenia wątku.|  
|[IRemoteDebugApplicationEvents::OnDestroyThread](../../winscript/reference/iremotedebugapplicationevents-ondestroythread.md)|Obsługuje zdarzenie zniszczone wątku.|  
|[IRemoteDebugApplicationEvents::OnBreakFlagChange](../../winscript/reference/iremotedebugapplicationevents-onbreakflagchange.md)|Obsługuje zdarzenie po zmianie flag podziału.|