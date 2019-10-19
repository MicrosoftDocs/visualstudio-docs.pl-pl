---
title: Interfejs IActiveScriptProfilerCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577299"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interfejs IActiveScriptProfilerCallback2
Dostarcza metody, które są używane przez aparat skryptów do powiadamiania obiektu profilera o wystąpieniu zdarzenia Document Object Model (DOM). Ten interfejs jest implementowany przez obiekt profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Powiadamia obiekt profilera, że aparat skryptów ma uruchamiać wywołanie funkcji modelu DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Powiadamia obiekt profilera, że aparat skryptów zakończył wywołanie funkcji DOM.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `IActiveScriptProfilerCallback2` po raz pierwszy w programie Internet Explorer 9.  
  
 Powiadomienia o wywołaniach funkcji, które nie są wywołaniami do modelu DOM, są dostarczane przez [interfejs IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Aby dodać możliwość uruchamiania i zatrzymywania profilowania, gdy skrypt jest uruchomiony, należy wywołać następujące metody. Korzystając z tych metod, można uzyskać kompletny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiona podczas uruchamiania lub zatrzymywania profilowania.  
> 
> - Wywołanie [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) w celu powiadomienia profilera o rozpoczęciu profilowania.  
>   - Zadzwoń do [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) w celu powiadomienia profilera o natychmiastowym zatrzymaniu profilowania.  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)