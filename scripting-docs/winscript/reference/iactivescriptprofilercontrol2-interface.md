---
title: Interfejs IActiveScriptProfilerControl2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571533"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>Interfejs IActiveScriptProfilerControl2
Zapewnia metody, które umożliwiają uruchamianie lub zatrzymywanie profilowania, gdy skrypt jest uruchomiony.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Powiadamia program profilujący o rozpoczęciu profilowania dla wszystkich odpowiednich aparatów skryptów. Dzięki temu można uzyskać kompletny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiony po rozpoczęciu profilowania.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Powiadamia program profilujący o zatrzymaniu profilowania dla wszystkich odpowiednich aparatów skryptów. Dzięki temu można uzyskać kompletny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiony po zatrzymaniu profilowania.|  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptProfilerControl   interfejsu](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)