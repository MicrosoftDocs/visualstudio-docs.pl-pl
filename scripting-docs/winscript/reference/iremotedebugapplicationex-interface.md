---
title: Interfejs IRemoteDebugApplicationEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9e25a28ade1ac73b9e4837dae61e2d91f24c45
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58144410"
---
# <a name="iremotedebugapplicationex-interface"></a>Interfejs IRemoteDebugApplicationEx
Reprezentuje uruchomionej aplikacji. Nie musi odpowiadać procesu systemu operacyjnego. Zazwyczaj debugera jest przeznaczony dla aplikacji do debugowania. Menedżer debugowania procesów zwykle implementuje obiektu aplikacji.  
  
 Oprócz metod odziedziczone `IUnknown`, `IRemoteDebugApplicationEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Zwraca identyfikator procesu aplikacji hosta.|  
|GetHostMachineName|Zwraca nazwę komputera, na którym działa aplikacja hosta na.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Określa język dla lokalizacji debugera.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Wymusza debugera w trybie pojedynczego kroku.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Odwołuje się polecenie break.|  
|SetProxyBlanketAndAddRef|Aktualizuje informacje o zabezpieczeniach COM na serwer proxy dla obiektu debugera do zapewnienia zgodności z funkcją debugowania zdalnego z systemem Windows 95 systemów operacyjnych.|  
|ReleaseFromSetProxyBlanket|AddRef wydań z SetProxyBlanketAndAddRef.|