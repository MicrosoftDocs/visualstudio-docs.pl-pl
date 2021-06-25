---
title: Wyrażenie ewaluatora | Microsoft Docs
description: Dowiedz się więcej na temat ewaluatorów wyrażeń, które badają składnię języka w celu analizowania i oceniania zmiennych i wyrażeń w czasie wykonywania w trybie przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 998f361d8008257cb8f4a888b4d4fbb985c9c977
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900983"
---
# <a name="expression-evaluator"></a>Wyrażenie
Ewaluatory wyrażeń (EE) badają składnię języka w celu analizowania i oceniania zmiennych i wyrażeń w czasie działania, dzięki czemu mogą być przeglądane przez użytkownika, gdy idee IDE są w trybie przerwania.

## <a name="use-expression-evaluators"></a>Korzystanie z ewaluatorów wyrażeń
 Wyrażenia są tworzone przy użyciu [metody ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) w następujący sposób:

1. Aparat debugowania implementuje interfejs [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. Pakiet debugowania pobiera obiekt z interfejsu `IDebugExpressionContext2` [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) a następnie wywołuje na nim metodę w celu uzyskania obiektu `IDebugStackFrame2::ParseText` [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

3. Pakiet debugowania wywołuje metodę [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [metodę EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) w celu uzyskania wartości wyrażenia. `IDebugExpression2::EvaluateAsync` Jest wywoływana z okna Polecenie/Bezpośrednie. Wszystkie inne składniki interfejsu użytkownika wywołują element `IDebugExpression2::EvaluateSync` .

4. Wynikiem oceny wyrażenia jest obiekt [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) który zawiera nazwę, typ i wartość wyniku oceny wyrażenia.

   Podczas oceny wyrażeń EE wymaga informacji ze składnika dostawcy symboli. Dostawca symboli dostarcza informacje symboliczne używane do identyfikowania i zrozumienia analizowanych wyrażeń.

   Po zakończeniu oceny wyrażeń asynchronicznych de wysyła zdarzenie asynchroniczne za pośrednictwem menedżera debugowania sesji (SDM) w celu powiadomienia środowiska IDE o zakończeniu oceny wyrażeń. Wynik oceny jest następnie zwracany z wywołania metody `IDebugExpression2::EvaluateSync` .

## <a name="implementation-notes"></a>Uwagi o implementacji
 Aparaty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania oczekują, że będą rozmawiały z ewaluatorem wyrażeń przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym ewaluator wyrażeń, który współpracuje z aparatami debugowania, musi obsługiwać clr (pełną listę wszystkich interfejsów debugowania CLR można znaleźć w pliku debugref.doc, który jest częścią [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
