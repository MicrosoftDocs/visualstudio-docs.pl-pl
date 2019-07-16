---
title: Ocenianie wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151620"
---
# <a name="evaluating-expressions"></a>Ocenianie wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyrażenia są tworzone na podstawie ciągi przekazywane z automatyczne, wyrażenie kontrolne, QuickWatch lub bezpośredniego systemu windows. Gdy wyrażenie jest obliczane, generuje drukowalnych ciąg, który zawiera nazwę i typ zmiennej lub argumentu i jego wartość. Ten ciąg jest wyświetlany w odpowiednie okno środowiska IDE.  
  
## <a name="implementation"></a>Implementacja  
 Wyrażenia są obliczane po zatrzymaniu w punkcie przerwania programu. Wyrażenia jest reprezentowany przez [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejs, który reprezentuje przeanalizowany wyrażenie, które jest gotowy do powiązania i oceniania w ramach oceny wyrażenia danego kontekstu. Ramka stosu Określa kontekst oceny wyrażeń dostarczający aparat debugowania (DE) przez zaimplementowanie [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.  
  
 Podany ciąg użytkownika i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu, aparat debugowania (DE) można uzyskać [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, przekazując ciąg użytkownika [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody. Zawracany interfejs IDebugExpression2 zawiera wyrażenie przeanalizowany, gotowy do oceny.  
  
 Za pomocą `IDebugExpression2` interfejsu, DE można uzyskać wartość wyrażenia przez Obliczanie wyrażenia synchroniczna lub asynchroniczna, za pomocą [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Tę wartość, wraz z nazwą i typ zmiennej lub argumentu, są wysyłane do IDE do wyświetlenia. Wartość, nazwę i typ są reprezentowane przez [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.  
  
 Do włączenia oceny wyrażenia, musi implementować DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsów. Ocena synchroniczne i asynchroniczne, wymagają wprowadzenia [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
