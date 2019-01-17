---
title: IActiveScriptProfilerControl Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7caa09f384ce460a3e73b21b10d6d8022182dde7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349494"
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