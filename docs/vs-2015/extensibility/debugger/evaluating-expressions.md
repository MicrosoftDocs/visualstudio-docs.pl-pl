---
title: Ocenianie wyrażeń | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151620"
---
# <a name="evaluating-expressions"></a>Ocenianie wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyrażenia są tworzone na podstawie ciągów przewidzianych z okna autostarts, Watch, QuickWatch lub Immediate. Gdy wyrażenie jest oceniane, generuje ciąg drukowalny, który zawiera nazwę i typ zmiennej lub argumentu i jego wartości. Ten ciąg jest wyświetlany w odpowiednim oknie środowiska IDE.  
  
## <a name="implementation"></a>Implementacja  
 Wyrażenia są oceniane, gdy program został zatrzymany w punkcie przerwania. Samo wyrażenie jest reprezentowane przez interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , który reprezentuje wyrażenie analizowane, które jest gotowe do powiązania i oceny w ramach danego kontekstu oceny wyrażenia. Ramka stosu określa kontekst oceny wyrażenia, który aparat debugowania (DE) dostarcza przez implementację interfejsu [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
 Po otrzymaniu ciągu użytkownika i interfejsu [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) aparat debugowania (de) może uzyskać Interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , przekazując ciąg użytkownika do metody [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . Zwrócony interfejs IDebugExpression2 zawiera wyrażenie analizowane gotowe do oceny.  
  
 Z `IDebugExpression2` interfejsem, de może uzyskać wartość wyrażenia za pośrednictwem synchronicznej lub asynchronicznej oceny wyrażenia, przy użyciu [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Ta wartość oraz nazwa i typ zmiennej lub argumentu są wysyłane do IDE w celu wyświetlenia. Wartość, nazwa i typ są reprezentowane przez interfejs [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 Aby włączyć szacowanie wyrażeń, element DE musi implementować interfejsy [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Obliczenia synchroniczne i asynchroniczne wymagają implementacji metody [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
