---
title: IActiveScriptProfilerCallback Interface | Microsoft Docs
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
ms.openlocfilehash: e8f64f187638af7f9ab4bf6b80e88fe6992c78e6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386088"
---
# <a name="iactivescriptprofilercallback-interface"></a>Interfejs IActiveScriptProfilerCallback
Udostępnia metody, które są używane przez silnik wykonywania skryptów, aby powiadomić obiekt profiler, po wystąpieniu zdarzenia. Ten interfejs jest implementowany przez obiekt profiler.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Wywoływane w celu zainicjowania obiektu profiler, zawsze wtedy, gdy rozpoczęto profilowanie na silnik wykonywania skryptów.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Wywołuje się, by bezpłatnych i wersji obiektu profilera po każdym zatrzymaniu profilowania na silnik wykonywania skryptów.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Powiadamia program profilujący, że obiekt, który aparat skryptów skompilowany skrypt.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Powiadamia program profilujący, że obiekt, który aparat skryptów napotkał funkcję, podczas kompilacji skryptu.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Powiadamia obiekt profiler, który ma wykonać wywołanie funkcji, która nie jest wywołaniem do modelu DOM (Document Object) silnik wykonywania skryptów.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Powiadamia program profilujący obiekt czy aparat skryptów zakończono wykonywanie funkcji wywołaniu, które nie jest wywołanie DOM.|  
  
## <a name="remarks"></a>Uwagi  
 Powiadomienie o wywołania funkcji do modelu DOM (Document Object) są dostarczane przez [interfejs IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
> Dodanie możliwości do uruchamiania i zatrzymywania profilowania, gdy skrypt jest uruchamiany, wywołaj następujące metody. Korzystając z tych metod, można uzyskać pełny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiona, uruchomienie lub zatrzymanie profilowania.  
> 
> - Wywołaj [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) powiadomić profiler rozpoczęto profilowanie.  
>   - Wywołaj [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) powiadomić profiler zostanie wkrótce zatrzymania profilowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)