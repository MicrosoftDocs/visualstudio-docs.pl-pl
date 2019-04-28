---
title: Interfejs IApplicationDebugger | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebugger interface
ms.assetid: 27f6f8f5-2bf3-49bc-8abb-dfca98935aba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1c0cc89c61665ce468457b64bbdd4b5d293649b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991453"
---
# <a name="iapplicationdebugger-interface"></a>Interfejs IApplicationDebugger
Podstawowy interfejs narażona jest debugera. Oprócz metod odziedziczone `IUnknown`, `IApplicationDebugger` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IApplicationDebugger::QueryAlive](../../winscript/reference/iapplicationdebugger-queryalive.md)|Wskazuje, czy debuger jest elastyczny.|  
|[IApplicationDebugger::CreateInstanceAtDebugger](../../winscript/reference/iapplicationdebugger-createinstanceatdebugger.md)|Umożliwia tworzenie obiektów w procesie debugowania przez kod to znaczy poza procesem do debugera.|  
|[IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)|Obsługuje zdarzenie danych wyjściowych debugowania.|  
|[IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)|Obsługuje zdarzenie punktu przerwania.|  
|[IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)|Obsługuje zdarzenie zamknięcia debugowania aplikacji.|  
|[IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)|Obsługuje zdarzenie aplikacji niestandardowych.|