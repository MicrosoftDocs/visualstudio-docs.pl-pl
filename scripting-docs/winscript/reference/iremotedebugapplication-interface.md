---
title: IRemoteDebugApplication Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a231818def210f7c88ab031059f8561c67b33d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944234"
---
# <a name="iremotedebugapplication-interface"></a>Interfejs IRemoteDebugApplication
Reprezentuje uruchomionej aplikacji. Nie musi odpowiadać do procesu systemu operacyjnego. Zazwyczaj debugera jest przeznaczony dla aplikacji do debugowania. Menedżer debugowania procesów zwykle implementuje obiektu aplikacji.  
  
 Oprócz metod odziedziczone `IUnknown`, `IRemoteDebugApplication` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Nadal aplikację, która jest obecnie dostępna w punkcie przerwania.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Powoduje, że aplikacja wkroczenia do debugera przy najbliższej sposobności.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Nawiązuje połączenie debugera do tej aplikacji.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Odłącza bieżący debuger z aplikacji.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Zwraca bieżący debuger jest podłączony do aplikacji.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Udostępnia mechanizm dla debugera IDE, działa poza procesem do aplikacji w celu tworzenia obiektów w procesie aplikacji.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Wskazuje, czy aplikacja jest elastyczny.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Wylicza wszystkie wątki, o których wiadomo, że są skojarzone z aplikacją.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Zwraca nazwę tego węzła aplikacji.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Zwracanie węzła aplikacji w ramach której są dodawane wszystkie węzły, powiązane z daną aplikacją.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Wylicza kontekstów wyrażenie globalne dla wszystkich języków, działające w tej aplikacji.|