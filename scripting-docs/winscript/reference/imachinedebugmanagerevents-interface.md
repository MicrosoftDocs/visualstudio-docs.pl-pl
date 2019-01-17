---
title: Interfejs IMachineDebugManagerEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344039"
---
# <a name="imachinedebugmanagerevents-interface"></a>Interfejs IMachineDebugManagerEvents
Sygnalizuje zmiany uruchomione listy aplikacji obsługiwane przez Menedżer debugowania maszyny. Ten interfejs może służyć przez debuger IDE do wyświetlania listy dynamicznych aplikacji.  
  
 Oprócz metod odziedziczone `IUnknown`, `IMachineDebugManagerEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Obsługuje zdarzenie, gdy aplikacja zostanie dodany do uruchamiania listy aplikacji.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Obsługuje zdarzenie, gdy aplikacja zostanie usunięty z uruchomionych listy aplikacji.|