---
title: Ocena wyrażeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738827"
---
# <a name="evaluate-expressions"></a>Ocena wyrażeń
Wyrażenia są tworzone na podstawie ciągów przekazywanych z okien **Autos**, **Watch**, **QuickWatch**lub **Immediate.** Po obliczeniu wyrażenia generuje ciąg do wydrukowania, który zawiera nazwę i typ zmiennej lub argumentu oraz jego wartość. Ten ciąg jest wyświetlany w odpowiednim oknie IDE.

## <a name="implementation"></a>Wdrażanie
 Wyrażenia są oceniane, gdy program został zatrzymany w punkcie przerwania. Samo wyrażenie jest reprezentowane przez interfejs [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) który reprezentuje analizowane wyrażenie, które jest gotowe do powiązania i oceny w kontekście oceny danego wyrażenia. Ramka stosu określa kontekst oceny wyrażenia, który dostarcza aparat debugowania (DE) implementując interfejs [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

 Biorąc pod uwagę ciąg użytkownika i interfejs [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) aparat debugowania (DE) można uzyskać interfejs [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) przekazując ciąg użytkownika do [metody IDebugExpressionContext2::ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Interfejs IDebugExpression2, który jest zwracany zawiera wyrażenie analizowane gotowe do oceny.

 Za `IDebugExpression2` pomocą interfejsu DE można uzyskać wartość wyrażenia za pomocą synchronicznej lub asynchronicznej oceny wyrażenia, przy użyciu [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Ta wartość, wraz z nazwą i typem zmiennej lub argumentu, jest wysyłana do IDE do wyświetlania. Wartość, nazwa i typ są reprezentowane przez interfejs [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

 Aby włączyć ocenę wyrażenia, DE musi implementować interfejsy [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) i [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Zarówno synchroniczne i asynchroniczne oceny wymagają implementacji [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody.

## <a name="see-also"></a>Zobacz też
- [Ramki stosu](../../extensibility/debugger/stack-frames.md)
- [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
