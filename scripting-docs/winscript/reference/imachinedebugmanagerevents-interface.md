---
title: Interfejs IMachineDebugManagerEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fcfcc2aed0fedefdc149b83e911d33cd3b54cdef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977633"
---
# <a name="imachinedebugmanagerevents-interface"></a>Interfejs IMachineDebugManagerEvents
Sygnalizuje zmiany uruchomione listy aplikacji obsługiwane przez Menedżer debugowania maszyny. Ten interfejs może służyć przez debuger IDE do wyświetlania listy dynamicznych aplikacji.  
  
 Oprócz metod odziedziczone `IUnknown`, `IMachineDebugManagerEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Obsługuje zdarzenie, gdy aplikacja zostanie dodany do uruchamiania listy aplikacji.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Obsługuje zdarzenie, gdy aplikacja zostanie usunięty z uruchomionych listy aplikacji.|