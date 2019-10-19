---
title: Interfejs IActiveScriptProfilerCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571713"
---
# <a name="iactivescriptprofilercallback-interface"></a>Interfejs IActiveScriptProfilerCallback
Dostarcza metody, które są używane przez aparat skryptów do powiadamiania obiektu profilera o wystąpieniu zdarzenia. Ten interfejs jest implementowany przez obiekt profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Wywołuje się, by zainicjować obiekt profilera po rozpoczęciu profilowania w aparacie skryptów.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Wywołuje się, by zwolnić i zwolnić obiekt profilera za każdym razem, gdy profilowanie zostanie zatrzymane w aparacie skryptów.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Powiadamia obiekt profilera, że skrypt skryptów skompilowany przez aparat skryptu.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Powiadamia obiekt profilera, że aparat skryptów napotkał funkcję podczas kompilowania skryptu.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Powiadamia obiekt profilera, że aparat skryptów ma wykonać wywołanie funkcji, które nie jest wywołaniem do Document Object Model (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Powiadamia obiekt profilera, że aparat skryptów zakończył wywołanie funkcji, która nie jest wywołaniem do modelu DOM.|  
  
## <a name="remarks"></a>Uwagi  
 Powiadomienia o wywołaniach funkcji do Document Object Model (DOM) są dostarczane przez [interfejs IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
> Aby dodać możliwość uruchamiania i zatrzymywania profilowania, gdy skrypt jest uruchomiony, należy wywołać następujące metody. Korzystając z tych metod, można uzyskać kompletny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiona podczas uruchamiania lub zatrzymywania profilowania.  
> 
> - Wywołanie [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) w celu powiadomienia profilera o rozpoczęciu profilowania.  
>   - Zadzwoń do [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) w celu powiadomienia profilera o natychmiastowym zatrzymaniu profilowania.  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)