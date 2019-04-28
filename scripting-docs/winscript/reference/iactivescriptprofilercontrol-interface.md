---
title: IActiveScriptProfilerControl Interface | Microsoft Docs
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
ms.openlocfilehash: 86f4fb8dea97930f717800a14a27740b76eb6c2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993062"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interfejs IActiveScriptProfilerControl
Implementowany przez aparat skryptów, który obsługuje profilowania. Zazwyczaj obiekt, który implementuje `IActiveScriptProfilerControl` implementuje również [IActiveScript](../../winscript/reference/iactivescript.md) interfejsu. W takim przypadku można uzyskać dojścia do `IActiveScriptProfilerControl` interfejsu, wywołując `IUnknown::QueryInterface` metody dla obiektu. Interfejs zapewnia metody niezbędne do zatrzymywania i uruchamiania profilowania w silnik wykonywania skryptów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Rozpoczyna się profilowanie na silnik wykonywania skryptów.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Umożliwia ustawienie maski zdarzeń programu profilującego w silnik wykonywania skryptów.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Zatrzymuje profilowanie na silnik wykonywania skryptów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)