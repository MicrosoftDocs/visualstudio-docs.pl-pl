---
title: Interfejs IEnumRemoteDebugApplicationThreads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads interface
ms.assetid: 4ae6f8ef-e7be-4e2d-9be4-e0cde0a70eb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d57e945593641036bbfbbecc90b790251c12075f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159546"
---
# <a name="ienumremotedebugapplicationthreads-interface"></a>Interfejs IEnumRemoteDebugApplicationThreads
Wylicza uruchomionych wątków w aplikacji.  
  
 Oprócz metod odziedziczone `IUnknown`, `IEnumRemoteDebugApplicationThreads` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumRemoteDebugApplicationThreads::Next](../../winscript/reference/ienumremotedebugapplicationthreads-next.md)|Pobiera określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumRemoteDebugApplicationThreads::Skip](../../winscript/reference/ienumremotedebugapplicationthreads-skip.md)|Pomija określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumRemoteDebugApplicationThreads::Reset](../../winscript/reference/ienumremotedebugapplicationthreads-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumRemoteDebugApplicationThreads::Clone](../../winscript/reference/ienumremotedebugapplicationthreads-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.|