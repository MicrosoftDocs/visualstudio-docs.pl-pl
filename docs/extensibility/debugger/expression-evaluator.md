---
title: Ewaluatora wyrażeń | Microsoft Docs
description: Dowiedz się więcej na temat ocen wyrażeń, które badają składnię języka, aby analizować i oceniać zmienne i wyrażenia w czasie wykonywania w trybie przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 6876bea4174df7f5ac293ea0d470f5922d7492d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055027"
---
# <a name="expression-evaluator"></a>Ewaluatora wyrażeń
Oceny wyrażeń (EE) sprawdzają składnię języka, aby analizować i oceniać zmienne i wyrażenia w czasie wykonywania, umożliwiając ich wyświetlanie przez użytkownika, gdy IDE jest w trybie przerwania.

## <a name="use-expression-evaluators"></a>Używanie ocen wyrażeń
 Wyrażenia są tworzone przy użyciu metody [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) w następujący sposób:

1. Aparat debugowania (DE) implementuje interfejs [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

2. Pakiet debugowania pobiera `IDebugExpressionContext2` obiekt z interfejsu [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , a następnie wywołuje `IDebugStackFrame2::ParseText` metodę na nim, aby uzyskać obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

3. Pakiet debugowania wywołuje metodę [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub metodę [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) w celu pobrania wartości wyrażenia. `IDebugExpression2::EvaluateAsync` jest wywoływany z okna polecenie/Immediate. Wszystkie inne składniki interfejsu użytkownika są wywoływane `IDebugExpression2::EvaluateSync` .

4. Wynik obliczania wyrażenia jest obiektem [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który zawiera nazwę, typ i wartość wyniku oceny wyrażenia.

   Podczas obliczania wyrażenia EE wymaga informacji od składnika dostawcy symboli. Dostawca symboli dostarcza informacje symboliczne służące do identyfikowania i analizowania wyanalizowanego wyrażenia.

   Po zakończeniu obliczania wyrażeń asynchronicznych przez cały czas przez Menedżera debugowania sesji (SDM) zostanie wysłane zdarzenie asynchroniczne, aby powiadomić IDE o ukończeniu oceny wyrażenia. Wynik obliczania jest następnie zwracany z wywołania `IDebugExpression2::EvaluateSync` metody.

## <a name="implementation-notes"></a>Uwagi o implementacji
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Aparaty debugowania oczekują na rozmowę z ewaluatora wyrażeń przy użyciu interfejsów aparatu plików wykonywalnych języka wspólnego (CLR). W związku z tym, ewaluatora wyrażeń, która współpracuje z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aparatami debugowania, musi obsługiwać środowisko CLR (kompletna lista wszystkich interfejsów debugowania CLR znajduje się w debugref.doc, który jest częścią [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
