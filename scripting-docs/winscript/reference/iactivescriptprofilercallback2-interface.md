---
title: IActiveScriptProfilerCallback2 Interface | Microsoft Docs
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
ms.openlocfilehash: d95c3db11551eb6551f509b4afbe52a70ff55ab9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145737"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interfejs IActiveScriptProfilerCallback2
Udostępnia metody, które są używane przez silnik wykonywania skryptów, aby powiadomić obiekt profiler, po wystąpieniu zdarzenia modelu DOM (Document Object). Ten interfejs jest implementowany przez obiekt profiler.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Powiadamia obiekt profiler, który silnik wykonywania skryptów przechodzi do uruchomienia wywołania funkcji DOM w LICZBIE.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Powiadamia program profilujący, że obiekt, który aparat skryptów Zakończono DOM wywołania funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 `IActiveScriptProfilerCallback2` Interfejsu najpierw wydane za pomocą programu Internet Explorer 9.  
  
 Powiadomienie o wywołania funkcji, które nie są wywołania do modelu DOM są dostarczane przez [interfejs IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Dodanie możliwości do uruchamiania i zatrzymywania profilowania, gdy skrypt jest uruchamiany, wywołaj następujące metody. Korzystając z tych metod, można uzyskać pełny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiona, uruchomienie lub zatrzymanie profilowania.  
> 
> - Wywołaj [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) powiadomić profiler rozpoczęto profilowanie.  
>   -   Wywołaj [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) powiadomić profiler zostanie wkrótce zatrzymania profilowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)