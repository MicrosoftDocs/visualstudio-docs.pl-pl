---
title: Interfejs IActiveScriptProfilerControl | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571599"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interfejs IActiveScriptProfilerControl
Zaimplementowane przez aparat obsługi skryptów obsługujący profilowanie. Zazwyczaj obiekt implementujący `IActiveScriptProfilerControl` również implementuje interfejs [IActiveScript](../../winscript/reference/iactivescript.md) . W takim przypadku można uzyskać uchwyt do interfejsu `IActiveScriptProfilerControl`, wywołując metodę `IUnknown::QueryInterface` dla obiektu. Interfejs udostępnia metody niezbędne do zatrzymywania i uruchamiania profilowania w aparacie skryptów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Uruchamia profilowanie w aparacie skryptów.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Ustawia maskę zdarzeń profilera w aparacie skryptów.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Powoduje zatrzymanie profilowania w aparacie obsługi skryptów.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)