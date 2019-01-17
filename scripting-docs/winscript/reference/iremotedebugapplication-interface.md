---
title: IRemoteDebugApplication Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 02ddf409bf25cb86fc742cdc004e2f1b664d22e3
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348766"
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