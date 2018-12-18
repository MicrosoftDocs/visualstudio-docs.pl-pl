---
title: Szacowanie wyrażeń (zestaw SDK debugowania programu Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb5bfe5f5c77e7ba1881f803830e1cb3d357561b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781585"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Obliczanie wyrażeń (zestaw SDK debugowania w programie Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W trybie break IDE musi umożliwiać można obliczyć wartości wyrażenia proste wielu zmiennych programu. Aby to osiągnąć, aparat debugowania (DE) musi umożliwiać do analizy i ocenić wyrażenie, które jest wprowadzany do jednego z okien środowiska IDE.  
  
 Wyrażenia są tworzone przy użyciu [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i są reprezentowane przez wynikowy [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.  
  
 **IDebugExpression2** interfejs jest implementowany przez DE i wywołuje jego **EvalAsync** metodę, aby zwrócić [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu środowiska IDE, aby wyświetlić wyniki oceny wyrażenia w środowisku IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca strukturę, który może służyć do umieszczenia wartości wyrażenia w oknie czujki lub okno zmiennych lokalnych.  
  
 Debugowanie pakietu lub sesja debugowania manager (SDM) wywołuje [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można pobrać [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wynik oceny. `IDebugProperty2` zawiera metody, które zwracają nazwa, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.  
  
## <a name="using-expression-evaluation"></a>Za pomocą oceny wyrażenia  
 Aby użyć obliczenia wyrażenia, należy zaimplementować [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i wszystkie metody [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, jak pokazano w poniższej tabeli.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza wyrażenie asynchronicznie.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy się obliczenia wyrażenia asynchroniczne.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|  
  
 Ocena synchroniczne i asynchroniczne, wymagają wprowadzenia [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Obliczanie wyrażenia asynchroniczne wymaga implementacji [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)

